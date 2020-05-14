---
title: Adicionando um comando à barra de ferramentas do Solution Explorer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740337"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Adicione um comando à barra de ferramentas do Solution Explorer
Este passo a passo mostra como adicionar um botão à barra de ferramentas **do Solution Explorer.**

 Qualquer comando em uma barra de ferramentas ou menu é chamado de botão no Visual Studio. Quando o botão é clicado, o código no manipulador de comando é executado. Normalmente, os comandos relacionados são agrupados para formar um grupo. Menus ou barras de ferramentas atuam como recipientes para grupos. A prioridade determina a ordem em que os comandos individuais em um grupo aparecem no menu ou na barra de ferramentas. Você pode impedir que um botão seja exibido na barra de ferramentas ou no menu controlando sua visibilidade. Um comando listado em `<VisibilityConstraints>` uma seção do arquivo *.vsct* aparece apenas no contexto associado. A visibilidade não pode ser aplicada aos grupos.

 Para obter mais informações sobre menus, comandos de barra de ferramentas e arquivos *.vsct,* consulte [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Use arquivos xml command table *(.vsct)* em vez de arquivos de configuração de tabela de comando *(.ctc)* para definir como menus e comandos aparecem em seus VSPackages. Para obter mais informações, consulte [Visual Studio Command Table (. Vsct) arquivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Crie uma extensão com um comando de menu
 Crie um projeto `SolutionToolbar`VSIX chamado . Adicione um modelo de item de comando de menu chamado **ToolbarButton**. Para obter informações sobre como fazer isso, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Adicione um botão à barra de ferramentas do Solution Explorer
 Esta seção do passo a passo mostra como adicionar um botão à barra de ferramentas **do Solution Explorer.** Quando o botão é clicado, o código no método de retorno de chamada é executado.

1. No arquivo *ToolbarButtonPackage.vsct,* vá `<Symbols>` para a seção. O `<GuidSymbol>` nó contém o grupo de menu e o comando gerados pelo modelo do pacote. Adicione `<IDSymbol>` um elemento a este nó para declarar o grupo que manterá seu comando.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. Na `<Groups>` seção, após a entrada do grupo existente, defina o novo grupo que você declarou na etapa anterior.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Definir o par GUID:ID `IDM_VS_TOOL_PROJWIN` pai e `guidSHLMainMenu` colocar esse grupo na barra de ferramentas do Solution **Explorer** e definir um valor de alta prioridade coloca-o após os outros grupos de comando.

3. Na `<Buttons>` seção, altere o ID pai da entrada gerada `<Button>` para refletir o grupo que você definiu na etapa anterior. O `<Button>` elemento modificado deve ser assim:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Compile o projeto e comece a depuração. A instância experimental aparece.

     A barra de ferramentas **do Solution Explorer** deve exibir o novo botão de comando à direita dos botões existentes. O ícone do botão é o strikethrough.

5. Clique no novo botão.

     Uma caixa de diálogo que tenha a mensagem **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback()** deve ser exibida.

## <a name="control-the-visibility-of-a-button"></a>Controle a visibilidade de um botão
 Esta seção do passo a passo mostra como controlar a visibilidade de um botão em uma barra de ferramentas. Ao definir um contexto para um `<VisibilityConstraints>` ou mais projetos na seção do arquivo *SolutionToolbar.vsct,* você restringe um botão para aparecer somente quando um projeto ou projetos estão abertos.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Para exibir um botão quando um ou mais projetos estão abertos

1. Na `<Buttons>` seção *toolbarButtonPackage.vsct*, adicione dois sinalizadores de comando ao elemento existente, `<Button>` entre as `<Strings>` `<Icons>` tags.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    As `DefaultInvisible` `DynamicVisibility` bandeiras devem ser definidas para `<VisibilityConstraints>` que as entradas na seção possam fazer efeito.

2. Crie `<VisibilityConstraints>` uma seção `<VisibilityItem>` que tenha duas entradas. Coloque a nova seção `</Commands>` logo após a tag de fechamento.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Cada item de visibilidade representa uma condição na qual o botão especificado é exibido. Para aplicar várias condições, você deve criar várias entradas para o mesmo botão.

3. Compile o projeto e comece a depuração. A instância experimental aparece.

    A barra de ferramentas **do Solution Explorer** não contém o botão de strikethrough.

4. Abra qualquer solução que contenha um projeto.

    O botão de strikethrough aparece na barra de ferramentas à direita dos botões existentes.

5. No menu **Arquivo** , clique em **Fechar Solução**. O botão desaparece da barra de ferramentas.

   A visibilidade do botão é [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] controlada até que o VSPackage seja carregado. Depois que o VSPackage é carregado, a visibilidade do botão é controlada pelo VSPackage.  Para obter mais informações, consulte [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Confira também
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
