---
title: Adicionando um menu de atalho em uma janela de ferramenta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740285"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Adicione um menu de atalho em uma janela de ferramenta
Este passo a passo coloca um menu de atalho em uma janela de ferramenta. Um menu de atalho é um menu que aparece quando um usuário clica com o botão, a caixa de texto ou o plano de fundo da janela. Os comandos em um menu de atalho se comportam da mesma forma que os comandos em outros menus ou barras de ferramentas. Para suportar um menu de atalho, especifique-o no arquivo *.vsct* e exiba-o em resposta ao clique com o botão direito do mouse.

Uma janela de ferramenta consiste em um controle do usuário WPF em uma classe de janela de ferramenta personalizada que herda de <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.

Este passo a passo mostra como criar um menu de atalho como um menu do Visual Studio, declarando itens de menu no arquivo *.vsct* e, em seguida, usando o ''''''Framework', para implementá-los na classe que define a janela da ferramenta. Essa abordagem facilita o acesso aos comandos do Visual Studio, elementos de IU e ao modelo de objeto satisfaço.

Alternativamente, se o menu de atalho não acessar a <xref:System.Windows.FrameworkElement.ContextMenu%2A> funcionalidade do Visual Studio, você poderá usar a propriedade de um elemento XAML no controle do usuário. Para obter mais informações, consulte [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Pré-requisitos
A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Criar o pacote de menu de atalho da janela da ferramenta

1. Crie um projeto `TWShortcutMenu` VSIX nomeado e adicione um modelo de janela de ferramenta chamado **ShortcutMenu** a ele. Para obter mais informações sobre como criar uma janela de ferramenta, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Especificando o menu de atalho
Um menu de atalho como o mostrado neste passo a passo permite que o usuário selecione a partir de uma lista de cores que são usadas para preencher o plano de fundo da janela da ferramenta.

1. Em *ShortcutMenuPackage.vsct,* encontre no elemento GuidSymbol chamado guidShortcutMenuPackageCmdSet e declare o menu de atalho, o grupo de menu de atalho e as opções de menu. O elemento GuidSymbol deve agora ser assim:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Pouco antes do elemento Botões, crie um elemento Menus e defina o menu de atalho nele.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Um menu de atalho não tem um pai porque não faz parte de um menu ou barra de ferramentas.

3. Crie um elemento Grupos com um elemento Grupo que contenha os itens do menu de atalho e associe o grupo ao menu de atalho.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. No elemento Botões, defina os comandos individuais que aparecerão no menu de atalho. O elemento Botões deve ser assim:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. Em *ShortcutMenuCommand.cs,* adicione as definições para o conjunto de comandoGUID, o menu de atalho e os itens do menu.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Estes são os mesmos IDs de comando definidos na seção Símbolos do arquivo *ShortcutMenuPackage.vsct.* O grupo de contexto não está incluído aqui porque é necessário apenas no arquivo *.vsct.*

## <a name="implementing-the-shortcut-menu"></a>Implementação do menu de atalho
 Esta seção implementa o menu de atalho e seus comandos.

1. Em *ShortcutMenu.cs,* a janela da ferramenta pode obter o serviço de comando do menu, mas o controle que ele contém não pode. As etapas a seguir mostram como disponibilizar o serviço de comando do menu ao controle do usuário.

2. Em *ShortcutMenu.cs,* adicione as seguintes diretivas usando:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Substituir o método Initialize() da janela da ferramenta para obter o serviço de comando do menu e adicionar o controle, passando o serviço de comando do menu para o construtor:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. No construtor de janelas da ferramenta ShortcutMenu, remova a linha que adiciona o controle. O construtor deve agora ficar assim:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. Em *ShortcutMenuControl.xaml.cs,* adicione um campo privado para o serviço de comando do menu e altere o construtor de controle para tomar o serviço de comando do menu. Em seguida, use o serviço de comando menu para adicionar os comandos do menu de contexto. O construtor ShortcutMenuControl deve agora parecer com o seguinte código. O manipulador de comando será definido mais tarde.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. Em *ShortcutMenuControl.xaml*, <xref:System.Windows.UIElement.MouseRightButtonDown> adicione um <xref:System.Windows.Controls.UserControl> evento ao elemento de nível superior. O arquivo XAML deve agora ser assim:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. Em *ShortcutMenuControl.xaml.cs,* adicione um stub para o manipulador de eventos.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Adicione as seguintes diretivas usando o mesmo arquivo:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implemente `MyToolWindowMouseRightButtonDown` o evento da seguinte forma.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Isso cria <xref:System.ComponentModel.Design.CommandID> um objeto para o menu de atalho, identifica a localização do clique <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> do mouse e abre o menu de atalho nesse local usando o método.

10. Implemente o manipulador de comando.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    Neste caso, apenas um método lida com eventos para todos os <xref:System.ComponentModel.Design.CommandID> itens do menu, identificando-o e definindo a cor de fundo de acordo. Se os itens do menu tivessem contido comandos não relacionados, você teria criado um manipulador de eventos separado para cada comando.

## <a name="test-the-tool-window-features"></a>Teste os recursos da janela da ferramenta

1. Compile o projeto e comece a depuração. A instância experimental aparece.

2. Na instância experimental, clique **em Exibir / Outros Windows**e, em seguida, clique em Menu de **atalho**. Fazer isso deve exibir a janela da ferramenta.

3. Clique com o botão direito do mouse no corpo da janela da ferramenta. Um menu de atalho que tenha uma lista de cores deve ser exibido.

4. Clique em uma cor no menu de atalho. A cor de fundo da janela da ferramenta deve ser alterada para a cor selecionada.

## <a name="see-also"></a>Confira também
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
- [Utilização e prestação de serviços](../extensibility/using-and-providing-services.md)
