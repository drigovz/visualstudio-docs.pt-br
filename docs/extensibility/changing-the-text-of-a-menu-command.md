---
title: Alterando o texto de um comando de menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739840"
---
# <a name="change-the-text-of-a-menu-command"></a>Alterar o texto de um comando menu
As etapas a seguir mostram como alterar o <xref:System.ComponentModel.Design.IMenuCommandService> rótulo de texto de um comando de menu usando o serviço.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Alterando um rótulo de comando de menu com o IMenuCommandService

1. Crie um projeto `MenuText` VSIX nomeado com um comando de menu chamado **ChangeMenuText**. Para obter mais informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. No arquivo *.vsct,* `TextChanges` adicione o sinalizador ao comando do menu, conforme mostrado no exemplo a seguir.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. No *arquivo ChangeMenuText.cs,* crie um manipulador de eventos que será chamado antes que o comando do menu seja exibido.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Você também pode atualizar o status do comando <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>menu <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>neste <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> método <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> alterando as propriedades e propriedades no objeto.

4. No construtor ChangeMenuText, substitua a inicialização e o código <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> de colocação de comando original por um código que cria um (em vez de um `MenuCommand`) que representa o comando menu, adiciona o <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> manipulador de eventos e dá o comando do menu ao serviço de comando do menu.

    Eis o que deveria parecer:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Compile o projeto e comece a depuração. A instância experimental do Visual Studio aparece.

6. No menu **Ferramentas,** você deve ver um comando chamado **Invocar ChangeMenuText**.

7. Clique no comando. Você deve ver a caixa de mensagens anunciando que **menuItemCallback** foi chamado. Ao descartar a caixa de mensagens, você deve ver que o nome do comando no menu Ferramentas agora é **Novo Texto**.
