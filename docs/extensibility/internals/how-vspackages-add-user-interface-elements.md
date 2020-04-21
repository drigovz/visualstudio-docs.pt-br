---
title: Como os VSPackages adicionam elementos de interface de usuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649591"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Como o VSPackages adiciona elementos de interface de usuário
Um VSPackage pode adicionar elementos de interface do usuário (UI), por exemplo, menus, barras de ferramentas e janelas de ferramentas, ao Visual Studio por meio do arquivo *.vsct.*

Você pode encontrar diretrizes de design para elementos de IU nas [diretrizes de experiência do usuário do Visual Studio.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="the-visual-studio-command-table-architecture"></a>A arquitetura da tabela de comando do Visual Studio
Como observado, a arquitetura da tabela de comando suporta os princípios arquitetônicos previstos. Os princípios por trás das abstrações, estruturas de dados e ferramentas da arquitetura da tabela de comando são os seguintes:

- Existem três tipos básicos de itens: menus, comandos e grupos. Os menus podem ser expostos na ui como menus, submenus, barras de ferramentas ou janelas de ferramentas. Os comandos são procedimentos que o usuário pode executar no IDE, e eles podem ser expostos como itens de menu, botões, caixas de lista ou outros controles. Os grupos são recipientes para menus e comandos.

- Cada item é especificado por uma definição que descreve o item, sua prioridade em relação a outros itens e as bandeiras que modificam seu comportamento.

- Cada item tem uma colocação que descreve o pai do item. Um item pode ter vários pais, para que possa aparecer em vários locais da ui.

Cada comando deve ter um grupo como seu pai, mesmo que seja o único filho nesse grupo. Todos os menus padrão também devem ter um grupo de pais. Barras de ferramentas e janelas de ferramentas agem como seus próprios pais. Um grupo pode ter como pai a barra principal do menu do Visual Studio, ou qualquer menu, barra de ferramentas ou janela de ferramenta.

### <a name="how-items-are-defined"></a>Como os itens são definidos
Um arquivo *.vsct* é formatado em XML. Ele define os elementos de UI para um pacote e determina onde esses elementos aparecem no IDE. Cada menu, grupo ou comando no pacote é primeiro atribuído `Symbols` um GUID e ID na seção. Durante todo o resto do arquivo *.vsct,* cada menu, comando e grupo é identificado por sua combinação GUID e ID. O exemplo a `Symbols` seguir mostra uma seção típica gerada pelo modelo de pacote do Visual Studio quando um **comando menu** é selecionado no modelo.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

O elemento de nível `Symbols` superior da seção é o [elemento GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol`elementos mapeiam nomes para GUIDs que são usados pelo IDE para identificar pacotes e suas partes componentes.

> [!NOTE]
> Os GUIDs são gerados automaticamente pelo modelo de pacote do Visual Studio. Você também pode criar um GUID exclusivo clicando em **Criar GUID** no menu **Ferramentas.**

O `GuidSymbol` primeiro `guid<PackageName>Pkg`elemento, é o GUID do pacote em si. Este é o GUID que é usado pelo Visual Studio para carregar o pacote. Normalmente, não tem elementos infantis.

Por convenção, menus e comandos são `GuidSymbol` agrupados sob um segundo elemento, `guid<PackageName>CmdSet`e bitmaps estão sob um terceiro `GuidSymbol` elemento, `guidImages`. Você não precisa seguir esta convenção, mas cada menu, grupo, comando e `GuidSymbol` bitmap devem ser filhos de um elemento.

No segundo `GuidSymbol` elemento, que representa o conjunto `IDSymbol` de comandos do pacote, estão vários elementos. Cada [elemento do IDSymbol](../../extensibility/idsymbol-element.md) mapeia um nome para um valor numérico e pode representar um menu, grupo ou comando que faz parte do conjunto de comandos. Os `IDSymbol` elementos `GuidSymbol` no terceiro elemento representam bitmaps que podem ser usados como ícones para comandos. Como os pares GUID/ID devem ser únicos em um `GuidSymbol` aplicativo, nenhum filho do mesmo elemento pode ter o mesmo valor.

### <a name="menus-groups-and-commands"></a>Menus, grupos e comandos
Quando um menu, grupo ou comando tem um GUID e ID, ele pode ser adicionado ao IDE. Cada elemento da UI deve ter as seguintes coisas:

- Um `guid` atributo que corresponde `GuidSymbol` ao nome do elemento em que o elemento ui é definido.

- Um `id` atributo que corresponde `IDSymbol` ao nome do elemento associado.

Juntos, `guid` os `id` e atributos compõem a *assinatura* do elemento UI.

- Um `priority` atributo que determina a colocação do elemento UI em seu menu ou grupo pai.

- Um [elemento](../../extensibility/parent-element.md) Pai `guid` que tem e `id` atributos que especificam a assinatura do menu ou grupo pai.

#### <a name="menus"></a>Menus
Cada menu é definido como `Menus` um elemento [Menu](../../extensibility/menu-element.md) na seção. Os menus `guid` `id`devem `priority` ter , e `Parent` atributos, e um elemento, e também os seguintes atributos adicionais e crianças:

- Um `type` atributo que especifica se o menu deve aparecer no IDE como uma espécie de menu ou como uma barra de ferramentas.

- Um [elemento Strings](../../extensibility/strings-element.md) que contém um [elemento ButtonText](../../extensibility/buttontext-element.md), que especifica o título do menu no IDE e um elemento [CommandName,](../../extensibility/commandname-element.md)que especifica o nome usado na janela **Comando** para acessar o menu.

- Bandeiras opcionais. Um [elemento CommandFlag](../../extensibility/command-flag-element.md) pode aparecer em uma definição de menu para alterar sua aparência ou comportamento no IDE.

Cada `Menu` elemento deve ter um grupo como seu pai, a menos que seja um elemento ancorável, como uma barra de ferramentas. Um menu dockable é seu próprio pai. Para obter mais informações sobre `type` menus e valores para o atributo, consulte a documentação do [elemento Menu.](../../extensibility/menu-element.md)

O exemplo a seguir mostra um menu que aparece na barra de menus do Visual Studio, ao lado do menu **Ferramentas.**

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Grupos
Um grupo é um item `Groups` definido na seção do arquivo *.vsct.* Grupos são apenas contêineres. Eles não aparecem no IDE, exceto como uma linha divisória em um menu. Portanto, um [elemento de Grupo](../../extensibility/group-element.md) é definido apenas por sua assinatura, prioridade e pai.

Um grupo pode ter um menu, outro grupo ou a si mesmo como pai. No entanto, o pai é tipicamente um menu ou barra de ferramentas. O menu no exemplo anterior é `IDG_VS_MM_TOOLSADDINS` uma criança do grupo, e esse grupo é uma criança da barra de menus do Visual Studio. O grupo no exemplo a seguir é um filho do menu no exemplo anterior.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Por fazer parte de um menu, esse grupo normalmente conteria comandos. No entanto, também pode conter outros menus. É assim que os submenus são definidos, como mostrado no exemplo a seguir.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Comandos
Um comando fornecido ao IDE é definido como um [elemento Button](../../extensibility/button-element.md) ou um [elemento Combo](../../extensibility/combo-element.md). Para aparecer em um menu ou em uma barra de ferramentas, o comando deve ter um grupo como pai.

##### <a name="buttons"></a>Botões
Os botões são `Buttons` definidos na seção. Qualquer item de menu, botão ou outro elemento que um usuário clique para executar um único comando é considerado um botão. Alguns tipos de botões também podem incluir a funcionalidade da lista. Os botões têm os mesmos atributos necessários e opcionais que os menus têm, e também podem ter um [elemento Ícone](../../extensibility/icon-element.md) que especifica o GUID e o ID do bitmap que representa o botão no IDE. Para obter mais informações sobre botões e seus atributos, consulte a documentação do [elemento Botões.](../../extensibility/buttons-element.md)

O botão no exemplo a seguir é um filho do grupo no exemplo anterior, e apareceria no IDE como um item de menu no menu pai desse grupo.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

##### <a name="combos"></a>Combos
Os combos são `Combos` definidos na seção. Cada `Combo` elemento representa uma caixa de lista baixa no IDE. A caixa de lista pode ou não ser escrita pelos `type` usuários, dependendo do valor do atributo do combo. Os combos têm os mesmos elementos e comportamento que os botões têm, e também podem ter os seguintes atributos adicionais:

- Um `defaultWidth` atributo que especifica a largura de pixel.

- Um `idCommandList` atributo que especifica uma lista que contém os itens exibidos na caixa de lista. A lista de comandos deve `GuidSymbol` ser declarada no mesmo nó que contém o combo.

O exemplo a seguir define um elemento combo.

```xml
<Combos>
  <Combo guid="guidFirstToolWinCmdSet"
         id="cmdidWindowsMediaFilename"
         priority="0x0100" type="DynamicCombo"
         idCommandList="cmdidWindowsMediaFilenameGetList"
         defaultWidth="130">
    <Parent guid="guidFirstToolWinCmdSet"
            id="ToolbarGroupID" />
    <CommandFlag>IconAndText</CommandFlag>
    <CommandFlag>CommandWellOnly</CommandFlag>
    <CommandFlag>StretchHorizontally</CommandFlag>
    <Strings>
      <CommandName>Filename</CommandName>
      <ButtonText>Enter a Filename</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

##### <a name="bitmaps"></a>Bitmaps
Os comandos que serão exibidos juntamente `Icon` com um ícone devem incluir um elemento que se refere a um bitmap usando seu GUID e ID. Cada bitmap é definido como um `Bitmaps` [elemento Bitmap](../../extensibility/bitmap-element.md) na seção. Os únicos atributos `Bitmap` necessários para uma definição são `guid` e `href`, que aponta para o arquivo de origem. Se o arquivo de origem for uma tira de recurso, um atributo **usedList** também é necessário para listar as imagens disponíveis na tira. Para obter mais informações, consulte a documentação do [elemento Bitmap.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Gerenciamento do domínio pai
As seguintes regras regem como um item pode chamar outro item como seu pai.

|Elemento|Definido nesta seção da Tabela de Comando|Pode ser contido (como pai, ou `CommandPlacements` por colocação na seção, ou ambos)|Pode conter (referido como um pai)|
|-------------| - | - | - |
|Agrupar|[Elemento de grupos,](../../extensibility/groups-element.md)o IDE, outros VSPackages|Um menu, um grupo, o próprio item|Menus, grupos e comandos|
|Menu|[Elemento menus,](../../extensibility/menus-element.md)o IDE, outros VSPackages|1 a *n* grupos|Grupos de 0 a *n*|
|Barra de ferramentas|[Elemento menus,](../../extensibility/menus-element.md)o IDE, outros VSPackages|O item em si|Grupos de 0 a *n*|
|Item de menu|[Elemento botões,](../../extensibility/buttons-element.md)o IDE, outros VSPackages|1 a *n* grupos, o item em si|-0 a *n* grupos|
|Botão|[Elemento botões,](../../extensibility/buttons-element.md)o IDE, outros VSPackages|1 a *n* grupos, o item em si||
|Combinação|[Elemento combos,](../../extensibility/combos-element.md)o IDE, outros VSPackages|1 a *n* grupos, o item em si||

### <a name="menu-command-and-group-placement"></a>Menu, comando e colocação em grupo
Um menu, grupo ou comando pode aparecer em mais de um local no IDE. Para que um item seja exibido em vários `CommandPlacements` locais, ele deve ser adicionado à seção como um [elemento CommandPlacement](../../extensibility/commandplacement-element.md). Qualquer menu, grupo ou comando pode ser adicionado como uma colocação de comando. No entanto, as barras de ferramentas não podem ser posicionadas dessa maneira porque não podem aparecer em vários locais sensíveis ao contexto.

As colocações `guid` `id`de `priority` comando têm , e atributos. O GUID e o ID devem coincidir com os do item que está posicionado. O `priority` atributo rege a colocação do item em relação a outros itens. Quando o IDE mescla dois ou mais itens com a mesma prioridade, suas colocações são indefinidas porque o IDE não garante que os recursos do pacote sejam lidos na mesma ordem toda vez que o pacote é construído.

Se um menu ou grupo aparecer em vários locais, todas as crianças desse menu ou grupo aparecerão em cada instância.

## <a name="command-visibility-and-context"></a>Visibilidade e contexto do comando
Quando vários VSPackages são instalados, uma profusão de menus, itens de menu e barras de ferramentas pode bagunçar o IDE. Para evitar esse problema, você pode controlar a visibilidade de elementos de iu física individuais usando *restrições de visibilidade* e bandeiras de comando.

### <a name="visibility-constraints"></a>Restrições de visibilidade
Uma restrição de visibilidade é definida como um `VisibilityConstraints` [elemento VisibilityItem](../../extensibility/visibilityitem-element.md) na seção. Uma restrição de visibilidade define contextos específicos de interface do reino em que o item de destino é visível. Um menu ou comando incluído nesta seção só é visível quando um dos contextos definidos estiver ativo. Se um menu ou comando não for referenciado nesta seção, ele será sempre visível por padrão. Esta seção não se aplica a grupos.

`VisibilityItem`os elementos devem ter três atributos, da seguinte forma: o `guid` elemento e `id` do elemento de ida e . `context` O `context` atributo especifica quando o item de destino será visível e toma qualquer contexto de interface do mundo válido como seu valor. As constantes de contexto de Interface <xref:Microsoft.VisualStudio.VSConstants> do Mundo para o Visual Studio são membros da classe. Cada `VisibilityItem` elemento pode ter apenas um valor de contexto. Para aplicar um segundo contexto, crie um segundo `VisibilityItem` elemento que aponte para o mesmo item, como mostrado no exemplo a seguir.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidSolutionToolbarCmdSet"
        id="cmdidTestCmd"
        context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

### <a name="command-flags"></a>Bandeiras de comando
Os seguintes sinalizadores de comando podem afetar a visibilidade dos menus e comandos a que se aplicam.

`AlwaysCreate`O menu é criado mesmo que não tenha grupos ou botões.

Válido para:`Menu`

`CommandWellOnly`Aplique este sinalizador se o comando não aparecer no menu de nível superior e você quiser disponibilizá-lo para personalização adicional do shell, por exemplo, vinculando-o a uma chave. Depois que o VSPackage for instalado, o usuário pode personalizar esses comandos abrindo a caixa de diálogo **Opções** e, em seguida, editando a colocação de comandos na categoria **Ambiente do Teclado.** Não afeta a colocação em menus de atalho, barras de ferramentas, controladores de menu ou submenus.

Válido para: `Button`,`Combo`

`DefaultDisabled`Por padrão, o comando será desativado se o VSPackage que implementa o comando não estiver carregado ou o método QueryStatus não tiver sido chamado.

Válido para: `Button`,`Combo`

`DefaultInvisible`Por padrão, o comando é invisível se o VSPackage que implementa o comando não estiver carregado ou o método QueryStatus não tiver sido chamado.

Deve ser combinado `DynamicVisibility` com a bandeira.

Válido `Button`para: `Combo`,`Menu`

`DynamicVisibility`A visibilidade do comando pode ser `QueryStatus` alterada usando o método ou `VisibilityConstraints` um GUID de contexto incluído na seção.

Aplica-se a comandos que aparecem nos menus, não nas barras de ferramentas. Os itens da barra de ferramentas de nível superior `OLECMDF_INVISIBLE` podem ser desativados, mas não ocultos, quando o sinalizador é devolvido do `QueryStatus` método.

Em um menu, este sinalizador também indica que ele deve ser automaticamente escondido quando seus membros estão escondidos. Esse sinalizador é normalmente atribuído a submenus porque menus de nível superior já têm esse comportamento.

Deve ser combinado `DefaultInvisible` com a bandeira.

Válido `Button`para: `Combo`,`Menu`

`NoShowOnMenuController`Se um comando que tem essa bandeira estiver posicionado em um controlador de menu, o comando não aparecerá na lista suspensa.

Válido para:`Button`

Para obter mais informações sobre sinalizadores de comando, consulte a documentação do [elemento CommandFlag.](../../extensibility/command-flag-element.md)

#### <a name="general-requirements"></a>Requisitos gerais
Seu comando deve passar pela seguinte série de testes antes de ser exibido e ativado:

- O comando está posicionado corretamente.

- A `DefaultInvisible` bandeira não está definida.

- O menu pai ou a barra de ferramentas são visíveis.

- O comando não é invisível por causa de uma entrada de contexto na seção elemento [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- VSPacote código que <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementa as exibições de interface e habilita seu comando. Nenhum código de interface interceptou e agiu nele.

- Quando um usuário clica no seu comando, ele fica sujeito ao procedimento que é descrito no [algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Chamada comandos pré-definidos
O [elemento UsedCommands](../../extensibility/usedcommands-element.md) permite que os VSPackages acessem comandos fornecidos por outros VSPackages ou pelo IDE. Para fazer isso, crie um [elemento UsedCommand](../../extensibility/usedcommand-element.md) que tenha o GUID e o ID do comando para usar. Isso garante que o comando será carregado pelo Visual Studio, mesmo que não faça parte da configuração atual do Visual Studio. Para obter mais informações, consulte [UsedCommand .](../../extensibility/usedcommand-element.md)

## <a name="interface-element-appearance"></a>Aparência do elemento de interface
Considerações para selecionar e posicionar elementos de comando são as seguintes:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferece muitos elementos de IU que aparecem de forma diferente dependendo da colocação.

- Um elemento de Interface do `DefaultInvisible` Usuário definido usando o sinalizador não será exibido no IDE a <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> menos que seja exibido pela implementação `VisibilityConstraints` do método VSPackage ou associado a um contexto de interface do usuário específico na seção.

- Mesmo um comando posicionado com sucesso pode não ser exibido. Isso porque o IDE oculta ou exibe automaticamente alguns comandos, dependendo das interfaces que o VSPackage implementou (ou não) implementou. Por exemplo, a implementação de algumas interfaces de compilação do VSPackage faz com que itens de menu relacionados à compilação sejam mostrados automaticamente.

- Aplicar o `CommandWellOnly` sinalizador na definição de elemento ui significa que o comando só pode ser adicionado por personalização.

- Os comandos podem estar disponíveis apenas em certos contextos de interface do e-mail, por exemplo, somente quando uma caixa de diálogo é exibida quando o IDE está em exibição de design.

- Para que certos elementos de interface do usuário sejam exibidos no IDE, você deve implementar uma ou mais interfaces ou escrever algum código.

## <a name="see-also"></a>Confira também
- [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md)
