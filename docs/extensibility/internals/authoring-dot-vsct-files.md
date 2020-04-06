---
title: Criação. Arquivos Vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709992"
---
# <a name="author-vsct-files"></a>Arquivos autor .vsct
Este documento mostra como criar um arquivo *.vsct* para adicionar itens de menu, barras de ferramentas e outros elementos de interface do usuário (UI) ao ambiente de desenvolvimento integrado do Visual Studio (IDE). Use essas etapas quando adicionar elementos de IA a um pacote Visual Studio (VSPackage) que ainda não tenha um arquivo *.vsct.*

 Para novos projetos, recomendamos que você use o modelo de pacote visual studio porque ele gera um arquivo *.vsct* que, dependendo de suas seleções, já tem os elementos necessários para um comando de menu, uma janela de ferramenta ou um editor personalizado. Você pode modificar este arquivo *.vsct* para atender aos requisitos do seu VSPackage. Para obter mais informações sobre como modificar um arquivo *.vsct,* consulte os exemplos em [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Autor do arquivo
 Autor de um arquivo *.vsct* nestas fases: Crie a estrutura para arquivos e recursos, declare os elementos de UI, coloque os elementos de UI no IDE e adicione quaisquer comportamentos especializados.

### <a name="file-structure"></a>Estrutura do arquivo
 A estrutura básica de um arquivo *.vsct* é um elemento raiz [commandTable](../../extensibility/commandtable-element.md) que contém um elemento [Comandos](../../extensibility/commands-element.md) e um elemento [Símbolos.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Para criar a estrutura do arquivo

1. Adicione um arquivo *.vsct* ao seu projeto seguindo as etapas de [Como: Criar um arquivo .vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Adicione os namespaces `CommandTable` necessários ao elemento, conforme mostrado no exemplo a seguir:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. No `CommandTable` elemento, adicione `Commands` um elemento para hospedar todos os seus menus personalizados, barras de ferramentas, grupos de comando e comandos. Para que seus elementos de iu personalizados possam carregar, o `Commands` elemento deve ter seu `Package` atributo definido para o nome do pacote.

     Após `Commands` o elemento, `Symbols` adicione um elemento para definir os GUIDs para o pacote e os nomes e iDs de comando para seus elementos de II.

### <a name="include-visual-studio-resources"></a>Inclua recursos do Visual Studio
 Use o elemento [Extern](../../extensibility/extern-element.md) para acessar os arquivos que definem os comandos do Visual Studio e os menus necessários para colocar seus elementos de II no IDE. Se você usar comandos definidos fora do pacote, use o elemento [UsedCommands](../../extensibility/usedcommands-element.md) para informar o Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Para incluir recursos do Visual Studio

1. Na parte superior `CommandTable` do elemento, adicione um `Extern` elemento para cada arquivo `href` externo a ser referenciado e defina o atributo ao nome do arquivo. Você pode referenciar os seguintes arquivos de cabeçalho para acessar os recursos do Visual Studio:

   - *Stdidcmd.h*: Define IDs para todos os comandos expostos pelo Visual Studio.

   - *Vsshlids.h*: Contém iDs de comando para menus do Visual Studio.

2. Se o pacote chamar os comandos definidos pelo Visual Studio `UsedCommands` ou `Commands` por outros pacotes, adicione um elemento após o elemento. Preencha este elemento com um elemento [UsedCommand](../../extensibility/usedcommand-element.md) para cada comando que você chama que não faz parte do seu pacote. Defina `guid` `id` os atributos dos `UsedCommand` elementos aos valores GUID e ID dos comandos a serem chamados.

   Para obter mais informações sobre como encontrar os GUIDs e IDs dos comandos do Visual Studio, consulte [GUIDs e IDs de comandos do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Para chamar comandos de outros pacotes, use o GUID e o ID do comando conforme definido no arquivo *.vsct* para esses pacotes.

### <a name="declare-ui-elements"></a>Declare elementos de UI
 Declare todos os novos `Symbols` elementos de iu na seção do arquivo *.vsct.*

#### <a name="to-declare-ui-elements"></a>Para declarar elementos de UI

1. No `Symbols` elemento, adicione três elementos [GuidSymbol.](../../extensibility/guidsymbol-element.md) Cada `GuidSymbol` elemento `name` tem um `value` atributo e um atributo. Defina `name` o atributo para que ele reflita o propósito do elemento. O `value` atributo requer um GUID. (Para gerar um GUID, no menu **Ferramentas,** selecione **Criar GUID**e, em seguida, selecione Formato **de Registro**.)

     O `GuidSymbol` primeiro elemento representa seu pacote, e normalmente não tem filhos. O `GuidSymbol` segundo elemento representa o conjunto de comandos e conterá todos os símbolos que definem seus menus, grupos e comandos. O `GuidSymbol` terceiro elemento representa sua armazenamento de imagens e contém símbolos para todos os ícones para seus comandos. Se você não tiver comandos que usem ícones, você pode omiti-lo o terceiro `GuidSymbol` elemento.

2. No `GuidSymbol` elemento que representa o seu conjunto de comandos, adicione um ou mais elementos [do IDSymbol.](../../extensibility/idsymbol-element.md) Cada um deles representa um menu, barra de ferramentas, grupo ou comando que você está adicionando à ui.

     Para `IDSymbol` cada elemento, `name` defina o atributo ao nome que você usará para se `value` referir ao menu, grupo ou comando correspondente e, em seguida, defina o elemento como um número hexadecimal que representará seu ID de comando. Nenhum `IDSymbol` elemento que tenha o mesmo pai pode ter o mesmo valor.

3. Se algum dos seus elementos de `IDSymbol` IA exigir ícones, adicione um elemento para cada ícone ao `GuidSymbol` elemento que representa sua armazenamento de imagens.

### <a name="put-ui-elements-in-the-ide"></a>Coloque elementos de UI no IDE
 Os [elementos Menus,](../../extensibility/menus-element.md) [Grupos](../../extensibility/groups-element.md)e [Botões](../../extensibility/buttons-element.md) contêm as definições de todos os menus, grupos e comandos definidos em seu pacote. Coloque esses menus, grupos e comandos no IDE usando um elemento [Pai,](../../extensibility/parent-element.md) que faz parte da definição de elemento de Interface do Usuário, ou usando um elemento [CommandPlacement](../../extensibility/commandplacement-element.md) que é definido em outro lugar.

 Cada `Menu` `Group`, `Button` e elemento `guid` tem `id` um atributo e um atributo. Sempre defina `guid` o atributo `GuidSymbol` para corresponder ao nome do elemento `id` que representa o `IDSymbol` seu conjunto de comandos e defina o atributo para o nome do elemento que representa seu menu, grupo ou comando na seção. `Symbols`

#### <a name="to-define-ui-elements"></a>Para definir elementos de UI

1. Se você estiver definindo novos menus, submenus, menus `Menus` de atalho `Commands` ou barras de ferramentas, adicione um elemento ao elemento. Em seguida, para cada menu a ser criado, adicione um elemento [Menu](../../extensibility/menu-element.md) ao `Menus` elemento.

    Defina `guid` `id` os atributos e atributos do `Menu` elemento e, em seguida, defina o atributo `type` para o tipo de menu que você deseja. Você também pode `priority` definir o atributo para estabelecer a posição relativa do menu no grupo pai.

   > [!NOTE]
   > O `priority` atributo não se aplica a barras de ferramentas e menus de contexto.

2. Todos os comandos do Visual Studio IDE devem ser hospedados por grupos de comando, que são as crianças diretas de menus e barras de ferramentas. Se você estiver adicionando novos menus ou barras de ferramentas ao IDE, estes devem conter novos grupos de comando. Você também pode adicionar grupos de comando a menus e barras de ferramentas existentes para que você possa agrupar visualmente seus comandos.

    Quando você adiciona novos grupos de `Groups` comando, você deve primeiro criar um elemento e, em seguida, adicionar a ele um elemento [de grupo](../../extensibility/group-element.md) para cada grupo de comando.

    Defina `guid` `id` os atributos e atributos de cada `Group` elemento e, em seguida, defina o atributo `priority` para estabelecer a posição relativa do grupo no menu pai. Para obter mais informações, consulte [Criar grupos reutilizáveis de botões](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Se você estiver adicionando novos comandos `Buttons` ao IDE, adicione um elemento ao `Commands` elemento. Em seguida, para cada [Button](../../extensibility/button-element.md) comando, `Buttons` adicione um elemento Button ao elemento.

   1. Defina `guid` `id` os atributos e atributos de cada `Button` elemento e, em seguida, defina o atributo `type` para o tipo de botão que você deseja. Você também pode `priority` definir o atributo para estabelecer a posição relativa do comando no grupo pai.

       > [!NOTE]
       > Use `type="button"` para comandos e botões de menu padrão nas barras de ferramentas.

   2. No `Button` elemento, adicione um elemento [Strings](../../extensibility/strings-element.md) que contém um elemento [ButtonText](../../extensibility/buttontext-element.md) e um elemento [CommandName.](../../extensibility/commandname-element.md) O `ButtonText` elemento fornece o rótulo de texto para um item do menu ou a dica de ferramenta para um botão de barra de ferramentas. O `CommandName` elemento fornece o nome do comando para usar bem no comando.

   3. Se o comando tiver um [Icon](../../extensibility/icon-element.md) ícone, crie `Button` um elemento `guid` Ícone `id` no elemento `Bitmap` e defina seus atributos ao elemento para o ícone.

       > [!NOTE]
       > Os botões da barra de ferramentas devem ter ícones.

   Para obter mais informações, consulte [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Se algum de seus comandos exigir ícones, `Commands` adicione um elemento [Bitmaps](../../extensibility/bitmaps-element.md) ao elemento. Em seguida, para cada ícone, adicione `Bitmaps` um elemento [Bitmap](../../extensibility/bitmap-element.md) ao elemento. É aqui que você especifica a localização do recurso bitmap. Para obter mais informações, consulte [Adicionar ícones aos comandos do menu](../../extensibility/adding-icons-to-menu-commands.md).

   Você pode contar com a estrutura de paternidade para colocar corretamente a maioria dos menus, grupos e comandos. Para conjuntos de comando muito grandes, ou quando um menu, grupo ou comando deve aparecer em vários lugares, recomendamos que você especifique a colocação de comando.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Para contar com a paternidade para colocar elementos de IU no IDE

1. Para uma paternidade `Parent` típica, `Menu`crie `Group`um `Command` elemento em cada um , e elemento definido em seu pacote.

    O alvo `Parent` do elemento é o menu ou grupo que conterá o menu, o grupo ou o comando.

   1. Defina `guid` o atributo `GuidSymbol` ao nome do elemento que define o conjunto de comandos. Se o elemento de destino não fizer parte do pacote, use a guia para esse conjunto de comandos, conforme definido no arquivo *.vsct* correspondente.

   2. Defina `id` o atributo para corresponder ao atributo `id` do menu ou grupo de destino. Para obter uma lista dos menus e grupos expostos pelo Visual Studio, consulte [GUIDs e IDs de menus do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ou [GUIDs e IDs de barras de ferramentas do Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Se você tiver um grande número de elementos de IA para colocar no IDE, ou se você tiver elementos que devem aparecer em vários lugares, defina suas colocações no elemento [CommandPlacements,](../../extensibility/commandplacements-element.md) conforme mostrado nas etapas seguintes.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Para usar a colocação de comando para colocar elementos de II no IDE

1. Após o elemento `Commands`, adicione um elemento `CommandPlacements`.

2. No `CommandPlacements` elemento, adicione `CommandPlacement` um elemento para cada menu, grupo ou comando para colocar.

    Cada `CommandPlacement` elemento `Parent` ou elemento coloca um menu, grupo ou comando em um local de IDE. Um elemento de IA só pode ter um pai, mas pode ter várias colocações de comando. Para colocar um elemento de IU `CommandPlacement` em vários locais, adicione um elemento para cada local.

3. Defina `guid` `id` os atributos de cada `CommandPlacement` elemento no menu ou `Parent` grupo de hospedagem, assim como você faria para um elemento. Você também pode `priority` definir o atributo para estabelecer a posição relativa do elemento UI.

   Você pode misturar colocação por paternidade e posicionamento de comando. No entanto, para conjuntos de comando muito grandes, recomendamos que você use apenas a colocação de comando.

### <a name="add-specialized-behaviors"></a>Adicionar comportamentos especializados
 Você pode usar o elemento [CommandFlag](../../extensibility/command-flag-element.md) para modificar o comportamento dos menus e comandos, por exemplo, para alterar sua aparência e visibilidade. Você também pode afetar quando um comando é visível usando o elemento [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) ou adicionar atalhos de teclado usando o elemento [KeyBindings.](../../extensibility/keybindings-element.md) Certos tipos de menus e comandos já possuem comportamentos especializados incorporados.

#### <a name="to-add-specialized-behaviors"></a>Para adicionar comportamentos especializados

1. Para tornar visível um elemento de interface do iu apenas em certos contextos de Interface do EI, por exemplo, quando uma solução é carregada, use restrições de visibilidade.

   1. Após o elemento `Commands`, adicione um elemento `VisibilityConstraints`.

   2. Para cada item de UI restringir, adicione um elemento [VisibilityItem.](../../extensibility/visibilityitem-element.md)

   3. Para `VisibilityItem` cada elemento, `guid` `id` defina os atributos e atributos `context` para o menu, grupo ou comando <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> e, em seguida, defina o atributo para o contexto de interface do usuário, conforme definido na classe.

2. Para definir a visibilidade ou disponibilidade de um item de II em código, use um ou mais dos seguintes sinalizadores de comando:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Para obter mais informações, consulte o elemento [CommandFlag.](../../extensibility/command-flag-element.md)

3. Para alterar a forma como um elemento aparece ou alterar sua aparência dinamicamente, use uma ou mais das seguintes bandeiras de comando:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Para obter mais informações, consulte o elemento [CommandFlag.](../../extensibility/command-flag-element.md)

4. Para alterar a forma como um elemento reage quando receber comandos, use uma ou mais das seguintes bandeiras de comando:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Para obter mais informações, consulte o elemento [CommandFlag.](../../extensibility/command-flag-element.md)

5. Para anexar um atalho de teclado dependente do menu a um menu ou a um item em um menu, adicione um caractere ampersand (&) no `ButtonText` elemento para o menu ou item do menu. O caractere que segue o ampersand é o atalho de teclado ativo quando o menu pai está aberto.

6. Para anexar um atalho de teclado independente do menu a um comando, use o elemento [KeyBindings.](../../extensibility/keybindings-element.md) Para obter mais informações, consulte o elemento [KeyBinding.](../../extensibility/keybinding-element.md)

7. Para localizar o texto `LocCanonicalName` do menu, use o elemento. Para obter mais informações, consulte o elemento [Strings.](../../extensibility/strings-element.md)

   Alguns tipos de menu e botão incluem comportamentos especializados. A lista a seguir descreve alguns tipos de menu e botão especializados. Para outros tipos, `types` consulte as descrições de atributos nos elementos [Menu](../../extensibility/menu-element.md), [Button](../../extensibility/button-element.md)e [Combo.](../../extensibility/combo-element.md)

   - Caixa de combinação: Uma caixa de combinação é uma lista de parada que pode ser usada em uma barra de ferramentas. Para adicionar caixas de combinação à ui, crie `Commands` um elemento [Combos](../../extensibility/combos-element.md) no elemento. Em seguida, `Combos` adicione `Combo` ao elemento um elemento para cada caixa de combinação para adicionar. `Combo`elementos têm os mesmos `Button` atributos `DefaultWidth` `idCommandList` e crianças como elementos e também têm e atributos. O `DefaultWidth` atributo define a largura `idCommandList` em pixels, e o atributo aponta para um ID de comando que é usado para preencher a caixa de combinação.

   - Controlador de menu: Um controlador de menu é um botão que tem uma seta ao lado. Clicar na seta abre uma lista. Para adicionar um controlador de menu `Menu` à ui, crie um elemento e defina seu `type` atributo para `MenuController` ou, `MenuControllerLatched`dependendo do comportamento que você deseja. Para preencher um controlador de menu, `Group` defina-o como o pai de um elemento. O controlador de menu exibirá todas as crianças desse grupo em sua lista de suspensos.

## <a name="see-also"></a>Confira também
- [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md)
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referência de esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
