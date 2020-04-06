---
title: Adicionando um Submenu a um Menu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740276"
---
# <a name="add-a-submenu-to-a-menu"></a>Adicionar um Submenu a um Menu
Este passo a passo baseia-se na demonstração em [Adicionar um menu à barra de menus do Visual Studio,](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) mostrando como adicionar um submenu ao menu **TestMenu.**

 Um submenu é um menu secundário que aparece em outro menu. Um submenu pode ser identificado pela seta que segue seu nome. Clicar no nome faz com que o submenu e seus comandos sejam exibidos.

 Este passo a passo cria um submenu em um menu na barra de menus do Visual Studio e coloca um novo comando no submenu. O passo a passo também implementa o novo comando.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Adicionar um Submenu a um Menu

1. Siga as etapas em [Adicionar um menu à barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) para criar o projeto e o item do menu. Os passos neste passo a passo assumem `TopLevelMenu`que o nome do projeto VSIX é .

2. Abrir *TestCommandPackage.vsct*. Na `<Symbols>` seção, `<IDSymbol>` adicione um elemento para o submenu, um para o grupo `<GuidSymbol>` submenu e outro para o comando, tudo no nó chamado "guidTopLevelMenuCmdSet". Este é o mesmo nó `<IDSymbol>` que contém o elemento para o menu de nível superior.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Adicione o submenu recém-criado à seção. `<Menus>`

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     O par GUID/ID do pai especifica o grupo de menu sustado gerado em [Adicionar um menu à barra de menu do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)e é filho do menu de nível superior.

4. Adicione o grupo de menu `<Groups>` definido na etapa 2 à seção e torne-o um filho do submenu.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Adicione um `<Button>` novo `<Buttons>` elemento à seção para definir o comando criado na etapa 2 como um item no submenu.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Compile a solução e inicie a depuração. Você deveria ver a instância experimental.

7. Clique **em 'Menu de teste'** para ver um novo submenu chamado **Sub Menu**. Clique **em SubMenu** para abrir o submenu e ver um novo comando, **Test Sub Command**. Observe que clicar **em Test Sub Command** não faz nada.

## <a name="add-a-command"></a>Adicionar um comando

1. Abra *TestCommand.cs* e adicione o seguinte ID de comando após o ID de comando existente.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Adicione o subcomando. Encontre o construtor de comando. Adicione as seguintes linhas logo `AddCommand` após a chamada ao método.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    O `SubItemCallback` manipulador de comando será definido mais tarde. O construtor deve agora ficar assim:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Adicione `SubItemCallback()`. Este é o método que é chamado quando o novo comando no submenu é clicado.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Compile o projeto e comece a depuração. A instância experimental deve aparecer.

5. No menu **TestMenu,** clique **em Sub Menu** e clique em **Sub-comando de teste**. Uma caixa de mensagens deve aparecer e exibir o texto, "Test Command Inside TestCommand.SubItemCallback()".

## <a name="see-also"></a>Confira também

- [Adicione um menu à barra de menus do Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
