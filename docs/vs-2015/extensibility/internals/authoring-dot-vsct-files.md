---
title: Criação. Arquivos vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85e466e7ebb6294a77e89040260c16fe0043e372
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838511"
---
# <a name="authoring-vsct-files"></a>Criar arquivos .Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este documento mostra como criar um arquivo. vsct para adicionar itens de menu, barras de ferramentas e outros elementos de interface do usuário ao IDE (ambiente de desenvolvimento integrado) do Visual Studio. Use estas etapas quando você adicionar elementos de interface do usuário a um pacote do Visual Studio (VSPackage) que ainda não tem um arquivo. vsct.  
  
 Para novos projetos, recomendamos que você use o modelo de pacote do Visual Studio porque ele gera um arquivo. vsct que, dependendo das suas seleções, já tem os elementos necessários para um comando de menu, uma janela de ferramentas ou um editor personalizado. Você pode modificar esse arquivo. vsct para atender aos requisitos de seu VSPackage. Para obter mais informações sobre como modificar um arquivo. vsct, consulte os exemplos em [estendendo menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Criando o arquivo  
 Crie um arquivo. vsct nestas fases: criar a estrutura para arquivos e recursos, declarar os elementos da interface do usuário, colocar os elementos da interface do usuário no IDE e adicionar qualquer comportamento especializado.  
  
### <a name="file-structure"></a>Estrutura de Arquivos  
 A estrutura básica de um arquivo. vsct é um elemento raiz [commandtable](../../extensibility/commandtable-element.md) que contém um elemento [Commands](../../extensibility/commands-element.md) e um elemento [Symbols](../../extensibility/symbols-element.md) .  
  
##### <a name="to-create-the-file-structure"></a>Para criar a estrutura do arquivo  
  
1. Adicione um arquivo. vsct ao seu projeto seguindo as etapas em [como: criar um. Arquivo vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2. Adicione os namespaces necessários ao `CommandTable` elemento, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3. No `CommandTable` elemento, adicione um `Commands` elemento para hospedar todos os seus menus, barras de ferramentas, grupos de comandos e comandos personalizados. Para que os elementos personalizados da interface do usuário possam ser carregados, o `Commands` elemento deve ter seu `Package` atributo definido como o nome do pacote.  
  
     Depois do `Commands` elemento, adicione um `Symbols` elemento para definir os GUIDs para o pacote e os nomes e IDs de comando para seus elementos de interface do usuário.  
  
### <a name="including-visual-studio-resources"></a>Incluindo recursos do Visual Studio  
 Use o elemento [externo](../../extensibility/extern-element.md) para acessar os arquivos que definem comandos do Visual Studio e os menus necessários para colocar os elementos da interface do usuário no IDE. Se você for usar comandos definidos fora do pacote, use o elemento [UsedCommands](../../extensibility/usedcommands-element.md) para informar ao Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Para incluir recursos do Visual Studio  
  
1. Na parte superior do `CommandTable` elemento, adicione um `Extern` elemento para cada arquivo externo a ser referenciado e defina o `href` atributo como o nome do arquivo. Você pode fazer referência aos seguintes arquivos de cabeçalho para acessar os recursos do Visual Studio:  
  
    - Stdidcmd. h define IDs para todos os comandos expostos pelo Visual Studio.  
  
    - Vsshlids. h, contém IDs de comando para menus do Visual Studio.  
  
2. Se o pacote chamar qualquer comando que seja definido pelo Visual Studio ou por outros pacotes, adicione um `UsedCommands` elemento após o `Commands` elemento. Preencha esse elemento com um elemento [UsedCommand](../../extensibility/usedcommand-element.md) para cada comando que você chamar que não faz parte do seu pacote. Defina os `guid` `id` atributos e dos `UsedCommand` elementos para os valores de GUID e ID dos comandos a serem chamados. Para obter mais informações sobre como localizar GUIDs e IDs de comandos do Visual Studio, consulte [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para chamar comandos de outros pacotes, use o GUID e a ID do comando, conforme definido no arquivo. vsct para esses pacotes.  
  
### <a name="declaring-ui-elements"></a>Declarando elementos da interface do usuário  
 Declare todos os novos elementos da interface do usuário na `Symbols` seção do arquivo. vsct.  
  
##### <a name="to-declare-ui-elements"></a>Para declarar elementos da interface do usuário  
  
1. No `Symbols` elemento, adicione três elementos [GuidSymbol](../../extensibility/guidsymbol-element.md) . Cada `GuidSymbol` elemento tem um `name` atributo e um `value` atributo. Defina o `name` atributo para que ele reflita a finalidade do elemento. O `value` atributo usa um GUID. (Para gerar um GUID, no menu **ferramentas** , clique em **Criar GUID**e selecione **formato do registro**.)  
  
     O primeiro `GuidSymbol` elemento representa seu pacote e normalmente não tem filhos. O segundo `GuidSymbol` elemento representa o conjunto de comandos e conterá todos os símbolos que definem seus menus, grupos e comandos. O terceiro `GuidSymbol` elemento representa o repositório de imagens e contém símbolos para todos os ícones de seus comandos. Se você não tiver comandos que usam ícones, poderá omitir o terceiro `GuidSymbol` elemento.  
  
2. No `GuidSymbol` elemento que representa o conjunto de comandos, adicione um ou mais elementos [IDSymbol](../../extensibility/idsymbol-element.md) . Cada uma delas representa um menu, barra de ferramentas, grupo ou comando que você está adicionando à interface do usuário.  
  
     Para cada `IDSymbol` elemento, defina o `name` atributo como o nome que você usará para se referir ao menu, grupo ou comando correspondente e, em seguida, defina o `value` elemento como um número hexadecimal que representará sua ID de comando. Dois `IDSymbol` elementos que têm o mesmo pai podem ter o mesmo valor.  
  
3. Se qualquer um dos elementos da interface do usuário exigir ícones, adicione um `IDSymbol` elemento para cada ícone ao `GuidSymbol` elemento que representa o repositório de imagens.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Colocando elementos da interface do usuário no IDE  
 O elemento [menus](../../extensibility/menus-element.md) , elemento [groups](../../extensibility/groups-element.md) e [Buttons](../../extensibility/buttons-element.md) contém as definições de todos os menus, grupos e comandos que são definidos em seu pacote. Coloque esses menus, grupos e comandos no IDE usando um elemento [pai](../../extensibility/parent-element.md) , que faz parte da definição do elemento de interface do usuário, ou usando um elemento [CommandPlacement](../../extensibility/commandplacement-element.md) que é definido em outro lugar.  
  
 Cada `Menu` `Group` elemento, e `Button` tem um `guid` atributo e um `id` atributo. Sempre defina o `guid` atributo para corresponder ao nome do `GuidSymbol` elemento que representa o conjunto de comandos e defina o `id` atributo como o nome do `IDSymbol` elemento que representa o menu, o grupo ou o comando na `Symbols` seção.  
  
##### <a name="to-define-ui-elements"></a>Para definir elementos da interface do usuário  
  
1. Se você estiver definindo novos menus, submenus, menus de atalho ou barras de ferramentas, adicione um `Menus` elemento ao `Commands` elemento. Em seguida, para cada menu a ser criado, adicione um elemento de [menu](../../extensibility/menu-element.md) ao `Menus` elemento.  
  
    Defina os `guid` `id` atributos e do elemento e, `Menu` em seguida, defina o `type` atributo como o tipo de menu desejado. Você também pode definir o `priority` atributo para estabelecer a posição relativa do menu no grupo pai.  
  
   > [!NOTE]
   > O `priority` atributo não se aplica a barras de ferramentas e menus de contexto.  
  
2. Todos os comandos no IDE do Visual Studio devem ser hospedados por grupos de comandos, que são filhos diretos de menus e barras de ferramentas. Se você estiver adicionando novos menus ou barras de ferramentas ao IDE, eles deverão conter novos grupos de comandos. Você também pode adicionar grupos de comandos a menus e barras de ferramentas existentes para que você possa agrupar visualmente seus comandos.  
  
    Ao adicionar novos grupos de comandos, você deve primeiro criar um `Groups` elemento e, em seguida, adicionar a ele um elemento de [grupo](../../extensibility/group-element.md) para cada grupo de comandos.  
  
    Defina os `guid` `id` atributos e de cada `Group` elemento e, em seguida, defina o `priority` atributo para estabelecer a posição relativa do grupo no menu pai. Para obter mais informações, consulte [criando grupos de botões reutilizáveis](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. Se você estiver adicionando novos comandos ao IDE, adicione um `Buttons` elemento ao `Commands` elemento. Em seguida, para cada comando, adicione um elemento [Button](../../extensibility/button-element.md) ao `Buttons` elemento.  
  
   1. Defina os `guid` `id` atributos e de cada `Button` elemento e, em seguida, defina o `type` atributo como o tipo de botão desejado. Você também pode definir o `priority` atributo para estabelecer a posição relativa do comando no grupo pai.  
  
      > [!NOTE]
      > Use `type="button"` para comandos de menu padrão e botões em barras de ferramentas.  
  
   2. No `Button` elemento, adicione um elemento [Strings](../../extensibility/strings-element.md) que contém um elemento [ButtonText](../../extensibility/buttontext-element.md) e um elemento [CommandName](../../extensibility/commandname-element.md) . O `ButtonText` elemento fornece o rótulo de texto para um item de menu ou a dica de ferramenta para um botão da barra de ferramentas. O `CommandName` elemento fornece o nome do comando a ser usado no bem do comando.  
  
   3. Se o comando tiver um ícone, crie um elemento [Icon](../../extensibility/icon-element.md) no elemento e `Button` defina seus `guid` `id` atributos e como o `Bitmap` elemento para o ícone.  
  
      > [!NOTE]
      > Os botões da barra de ferramentas devem ter ícones.  
  
      Para obter mais informações, consulte [MenuCommands vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4. Se qualquer um dos seus comandos exigir ícones, adicione um elemento [bitmaps](../../extensibility/bitmaps-element.md) ao `Commands` elemento. Em seguida, para cada ícone, adicione um elemento [bitmap](../../extensibility/bitmap-element.md) ao `Bitmaps` elemento. É aqui que você especifica o local do recurso de bitmap. Para obter mais informações, consulte [adicionando ícones a comandos de menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Você pode contar com a estrutura de pais para posicionar corretamente a maioria dos menus, grupos e comandos. Para conjuntos de comandos muito grandes ou quando um menu, grupo ou comando deve aparecer em vários locais, recomendamos que você especifique o posicionamento do comando.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Para contar com o pai para posicionar elementos de interface do usuário no IDE  
  
1. Para o pai típico, crie um `Parent` elemento em cada `Menu` `Group` elemento, e `Command` que esteja definido em seu pacote.  
  
    O destino do `Parent` elemento é o menu ou grupo que conterá o menu, o grupo ou o comando.  
  
   1. Defina o `guid` atributo como o nome do `GuidSymbol` elemento que define o conjunto de comandos. Se o elemento de destino não fizer parte do seu pacote, use o GUID para esse conjunto de comandos, conforme definido no arquivo. vsct correspondente.  
  
   2. Defina o `id` atributo para corresponder ao `id` atributo do menu ou grupo de destino. Para obter uma lista dos menus e grupos expostos pelo Visual Studio, consulte [GUIDs e IDs de menus](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou GUIDs do Visual Studio [e IDs das barras de ferramentas do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Se você tiver um grande número de elementos da interface do usuário para colocar no IDE ou se tiver elementos que devem aparecer em vários locais, defina seus posicionamentos no elemento [CommandPlacements](../../extensibility/commandplacements-element.md) , conforme mostrado nas etapas a seguir.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar o posicionamento de comando para colocar elementos de interface do usuário no IDE  
  
1. Após o elemento `Commands`, adicione um elemento `CommandPlacements`.  
  
2. No `CommandPlacements` elemento, adicione um `CommandPlacement` elemento para cada menu, grupo ou comando a ser colocado.  
  
    Cada `CommandPlacement` elemento ou `Parent` elemento coloca um menu, grupo ou comando em um único local do IDE. Um elemento de interface do usuário só pode ter um pai, mas pode ter vários posicionamentos de comandos. Para posicionar um elemento de interface do usuário em vários locais, adicione um `CommandPlacement` elemento para cada local.  
  
3. Defina os `guid` `id` atributos e de cada `CommandPlacement` elemento para o menu ou grupo de hospedagem, assim como você faria com um `Parent` elemento. Você também pode definir o `priority` atributo para estabelecer a posição relativa do elemento de interface do usuário.  
  
   Você pode misturar o posicionamento por pais e posicionamento de comando. No entanto, para conjuntos de comandos muito grandes, recomendamos que você use apenas posicionamento de comando.  
  
### <a name="adding-specialized-behaviors"></a>Adicionando comportamentos especializados  
 Você pode usar elementos [CommandFlag](../../extensibility/command-flag-element.md) para modificar o comportamento de menus e comandos, por exemplo, para alterar sua aparência e visibilidade. Você também pode afetar quando um comando é visível usando [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)ou adicionar atalhos de teclado usando [associações](../../extensibility/keybindings-element.md)de teclas. Determinados tipos de menus e comandos já têm comportamentos especializados internos.  
  
##### <a name="to-add-specialized-behaviors"></a>Para adicionar comportamentos especializados  
  
1. Para tornar um elemento de interface do usuário visível apenas em determinados contextos da interface do usuário, por exemplo, quando uma solução é carregada, use restrições de visibilidade.  
  
   1. Após o elemento `Commands`, adicione um elemento `VisibilityConstraints`.  
  
   2. Para cada item da interface do usuário a ser restringido, adicione um elemento [VisibilityItem](../../extensibility/visibilityitem-element.md) .  
  
   3. Para cada `VisibilityItem` elemento, defina os `guid` `id` atributos e para o menu, grupo ou comando e, em seguida, defina o `context` atributo como o contexto de interface do usuário desejado, conforme definido na <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> classe. Para obter mais informações, consulte [elemento VisibilityItem](../../extensibility/visibilityitem-element.md).  
  
2. Para definir a visibilidade ou a disponibilidade de um item de interface do usuário no código, use um ou mais dos seguintes sinalizadores de comando:  
  
   - Defaultdesabilitoud  
  
   - Invisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     Para obter mais informações, consulte [elemento de sinalizador de comando](../../extensibility/command-flag-element.md).  
  
3. Para alterar o modo como um elemento é exibido ou alterar sua aparência dinamicamente, use um ou mais dos seguintes sinalizadores de comando:  
  
   - AlwaysCreate  
  
   - CommandWellOnly  
  
   - Defaultdocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - Otimizar  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - Textchanges  
  
   - TextOnly  
  
     Para obter mais informações, consulte [elemento de sinalizador de comando](../../extensibility/command-flag-element.md).  
  
4. Para alterar a forma como um elemento reage quando recebe comandos, use um ou mais dos seguintes sinalizadores de comando:  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - Ativar  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - Exec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     Para obter mais informações, consulte [elemento de sinalizador de comando](../../extensibility/command-flag-element.md).  
  
5. Para anexar um atalho de teclado dependente de menu a um menu ou item em um menu, adicione um caractere de e comercial (' & ') no `ButtonText` elemento para o menu ou item de menu. O caractere que segue o e comercial é o atalho de teclado ativo quando o menu pai está aberto.  
  
6. Para anexar um atalho de teclado independente de menu a um comando, use [keybindings](../../extensibility/keybindings-element.md). Para obter mais informações, consulte [elemento KeyBinding](../../extensibility/keybinding-element.md).  
  
7. Para localizar o texto do menu, use o `LocCanonicalName` elemento. Para obter mais informações, consulte [elemento Strings](../../extensibility/strings-element.md).  
  
   Alguns tipos de menu e de botão incluem comportamentos especializados. A tabela a seguir descreve alguns tipos de menus e botões especializados. Para outros tipos, consulte as `types` descrições de atributo no [elemento de menu](../../extensibility/menu-element.md), no [elemento Button](../../extensibility/button-element.md)e no [elemento de combinação](../../extensibility/combo-element.md).  
  
   Caixa de combinação  
   Uma caixa de combinação é uma lista suspensa que pode ser usada em uma barra de ferramentas. Para adicionar caixas de combinação à interface do usuário, crie um elemento de [combinação](../../extensibility/combos-element.md) no `Commands` elemento. Em seguida, adicione ao `Combos` elemento um `Combo` elemento para cada caixa de combinação a ser adicionada. `Combo` os elementos têm os mesmos atributos e filhos que os `Button` elementos e também têm `DefaultWidth` `idCommandList` atributos e. O `DefaultWidth` atributo define a largura em pixels e o `idCommandList` atributo aponta para uma ID de comando que é usada para preencher a caixa de combinação. Para obter mais informações, consulte a `Combo` documentação do elemento.  
  
   MenuController  
   Um controlador de menu é um botão que tem uma seta ao lado dele. Clicar na seta abre uma lista. Para adicionar um controlador de menu à interface do usuário, crie um `Menu` elemento e defina seu `type` atributo como **MenuController** ou **MenuControllerLatched**, dependendo do comportamento desejado. Para preencher um controlador de menu, defina-o como o pai de um `Group` elemento. O controlador de menu exibirá todos os filhos desse grupo em sua lista suspensa.  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo menus e comandos](../../extensibility/extending-menus-and-commands.md)   
 [Tabela de comandos do Visual Studio (. Arquivos de vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)
