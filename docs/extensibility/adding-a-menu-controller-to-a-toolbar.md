---
title: Adicionando um controlador de menu a uma barra de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740322"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Adicione um controlador de menu a uma barra de ferramentas
Este passo a passo se constrói na [barra de ferramentas Adicionar uma barra de ferramentas a um](../extensibility/adding-a-toolbar-to-a-tool-window.md) passo a passo da janela da ferramenta e mostra como adicionar um controlador de menu à barra de ferramentas da janela da ferramenta. As etapas aqui mostradas também podem ser aplicadas à barra de ferramentas criada no Passo a Passo de [Adicionar uma barra de](../extensibility/adding-a-toolbar.md) ferramentas.

Um controlador de menu é um controle dividido. O lado esquerdo do controlador de menu mostra o comando usado pela última vez, e você pode executá-lo clicando nele. O lado direito do controlador de menu é uma seta que, quando clicada, abre uma lista de comandos adicionais. Quando você clica em um comando na lista, o comando é executado e ele substitui o comando no lado esquerdo do controlador de menu. Desta forma, o controlador de menu opera como um botão de comando que sempre mostra o último comando usado de uma lista.

Os controladores de menu podem aparecer nos menus, mas são mais usados em barras de ferramentas.

## <a name="prerequisites"></a>Pré-requisitos
A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-controller"></a>Criar um controlador de menu

1. Siga os procedimentos descritos em [Adicionar uma barra de ferramentas a uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) para criar uma janela de ferramenta que tenha uma barra de ferramentas.

2. Em *TWTestCommandPackage.vsct,* vá para a seção Símbolos. No elemento GuidSymbol chamado **guidTWTestCommandPackageCmdSet,** declare seu controlador de menu, grupo controlador de menu e três itens de menu.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Na seção Menus, após a última entrada do menu, defina o controlador de menu suscitado como um menu.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Os `TextChanges` `TextIsAnchorCommand` sinalizadores devem ser incluídos para permitir que o controlador de menu reflita o último comando selecionado.

4. Na seção Grupos, após a última entrada do grupo, adicione o grupo controlador de menu.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Ao definir o controlador de menucomo o pai, quaisquer comandos colocados neste grupo aparecem no controlador de menus. O `priority` atributo é omitido, o que o define para o valor padrão de 0, porque é o único grupo no controlador de menu.

5. Na seção Botões, após a última entrada do botão, adicione um elemento Botão para cada um dos itens do menu.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. Neste ponto, você pode olhar para o controlador de menu. Compile o projeto e comece a depuração. Você deveria ver a instância experimental.

   1. No **menu Exibir / Outros Windows,** abra **Test ToolWindow**.

   2. O controlador de menu aparece na barra de ferramentas na janela da ferramenta.

   3. Clique na seta no lado direito do controlador de menu para ver os três comandos possíveis.

      Observe que quando você clica em um comando, o título do controlador de menu muda para exibir esse comando. Na próxima seção, adicionaremos o código para ativar esses comandos.

## <a name="implement-the-menu-controller-commands"></a>Implementar os comandos do controlador de menu

1. Em *TWTestCommandPackageGuids.cs,* adicione IDs de comando para seus três itens de menu após os IDs de comando existentes.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. Em *TWTestCommand.cs,* adicione o seguinte código `TWTestCommand` no topo da classe.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. No construtor TWTestCommand, após a última `AddCommand` chamada ao método, adicione código para rotear os eventos para cada comando através dos mesmos manipuladores.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Adicione um manipulador de eventos à classe **TWTestCommand** para marcar o comando selecionado conforme verificado.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Adicione um manipulador de eventos que exibe uma MessageBox quando o usuário seleciona um comando no controlador de menu:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Testando o controlador de menu

1. Compile o projeto e comece a depuração. Você deveria ver a instância experimental.

2. Abra a **Janela de Ferramentas de Teste** no menu Exibir / Outros **Windows.**

    O controlador de menu aparece na barra de ferramentas na janela da ferramenta e exibe **o ITEM 1**do MC .

3. Clique no botão do controlador de menu à esquerda da seta.

    Você deve ver três itens, o primeiro dos quais é selecionado e tem uma caixa de destaque em torno de seu ícone. Clique **em MC Item 3**.

    Uma caixa de diálogo é exibida com a mensagem **Você selecionou o controlador de menu Item 3**. Observe que a mensagem corresponde ao texto no botão controlador do menu. O botão do controlador de menu agora exibe **o ITEM 3**do MC .

## <a name="see-also"></a>Confira também
- [Adicionando uma barra de ferramentas a uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Adicionando uma barra de ferramentas](../extensibility/adding-a-toolbar.md)
