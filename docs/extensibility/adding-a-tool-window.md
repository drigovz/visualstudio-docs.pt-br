---
title: Adicionando uma janela de ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740260"
---
# <a name="add-a-tool-window"></a>Adicionar uma janela de ferramenta

Neste passo a passo você aprende como criar uma janela de ferramentas e integrá-la ao Visual Studio das seguintes maneiras:

- Adicione um controle à janela da ferramenta.

- Adicione uma barra de ferramentas a uma janela de ferramenta.

- Adicione um comando à barra de ferramentas.

- Implemente os comandos.

- Defina a posição padrão para a janela da ferramenta.

## <a name="prerequisites"></a>Pré-requisitos

O Visual Studio SDK está incluído como um recurso opcional na configuração do Visual Studio. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Criar uma janela de ferramenta

1. Crie um projeto chamado **FirstToolWin** usando o modelo VSIX e adicione um modelo de item de janela de ferramenta personalizado chamado **FirstToolWindow**.

    > [!NOTE]
    > Para obter mais informações sobre como criar uma extensão com uma janela de ferramenta, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Adicione um controle à janela da ferramenta

1. Remova o controle padrão. Abra *firstToolWindowControl.xaml* e exclua o **Clique em Mim!** .

2. Na **caixa de ferramentas,** expanda a seção **Todos os Controles wpf** e arraste o controle **do Elemento de mídia** para o formulário **FirstToolWindowControl.** Selecione o controle e, na janela **Propriedades,** nomeie este elemento **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Adicione uma barra de ferramentas à janela da ferramenta
Adicionando uma barra de ferramentas da seguinte maneira, você garante que seus gradientes e cores são consistentes com o resto do IDE.

1. No **Solution Explorer,** abra *FirstToolWindowPackage.vsct*. O arquivo *.vsct* define os elementos de interface gráfica do usuário (GUI) na janela da ferramenta usando XML.

2. Na `<Symbols>` seção, `<GuidSymbol>` encontre o `name` nó `guidFirstToolWindowPackageCmdSet`cujo atributo é . Adicione os `<IDSymbol>` dois elementos `<IDSymbol>` a seguir à lista de elementos neste nó para definir uma barra de ferramentas e um grupo de barras de ferramentas.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Logo acima `<Buttons>` da seção, crie uma `<Menus>` seção que se assemelhe a isso:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Existem vários tipos diferentes de menu. Este menu é uma barra de ferramentas `type` em uma janela de ferramenta, definida por seu atributo. As `guid` `id` configurações compõem o ID totalmente qualificado da barra de ferramentas. Normalmente, `<Parent>` o menu de um menu é o grupo de contenção. No entanto, uma barra de ferramentas é definida como seu próprio pai. Portanto, o mesmo identificador é `<Menu>` `<Parent>` usado para e elementos. O `priority` atributo é apenas '0'.

4. As barras de ferramentas se assemelham aos menus de muitas maneiras. Por exemplo, assim como um menu pode ter grupos de comandos, as barras de ferramentas também podem ter grupos. (Nos menus, os grupos de comando são separados por linhas horizontais. Nas barras de ferramentas, os grupos não são separados por divisores visuais.)

    Adicione `<Groups>` uma seção `<Group>` que contenha um elemento. Isso define o grupo cujo ID `<Symbols>` você declarou na seção. Adicione `<Groups>` a seção `<Menus>` logo após a seção.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Ao definir o GUID e o ID pai no GUID e ID da barra de ferramentas, você adiciona o grupo à barra de ferramentas.

## <a name="add-a-command-to-the-toolbar"></a>Adicione um comando à barra de ferramentas

Adicione um comando à barra de ferramentas, que é exibida como um botão.

1. Na `<Symbols>` seção, declare os seguintes elementos do IDSymbol logo após as declarações do grupo de barras de ferramentas e da barra de ferramentas.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Adicione um elemento `<Buttons>` Button dentro da seção. Este elemento aparecerá na barra de ferramentas na janela da ferramenta, com um ícone **De pesquisa** (lupa).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Abra *FirstToolWindowCommand.cs* e adicione as seguintes linhas na classe logo após os campos existentes.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Fazer isso torna seus comandos disponíveis em código.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Adicione uma propriedade mediaplayer ao FirstToolWindowControl
A partir dos manipuladores de eventos para os controles da barra de ferramentas, seu código deve ser capaz de acessar o controle do Media Player, que é filho da classe FirstToolWindowControl.

No **Solution Explorer,** clique com o botão direito do mouse *FirstToolWindowControl.xaml,* clique **em 'Código de exibição'** e adicione o código a seguir à classe FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Instanciar a janela da ferramenta e a barra de ferramentas
Adicione uma barra de ferramentas e um comando de menu que invoca a caixa de diálogo **Arquivo Aberto** e reproduz o arquivo de mídia selecionado.

1. Abra *FirstToolWindow.cs* e `using` adicione as seguintes diretivas:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. Dentro da classe FirstToolWindow, adicione uma referência pública ao controle FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. No final do construtor, defina essa variável de controle para o controle recém-criado.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Instanciar a barra de ferramentas dentro do construtor.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. Neste ponto, o construtor FirstToolWindow deve ficar assim:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Adicione o comando menu à barra de ferramentas. Na classe FirstToolWindowCommand.cs, adicione a seguinte diretiva usando:

    ```csharp
    using System.Windows.Forms;
    ```

7. Na classe FirstToolWindowCommand, adicione o seguinte código no final do método ShowToolWindow(). O comando ButtonHandler será implementado na próxima seção.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Para implementar um comando de menu na janela da ferramenta

1. Na classe FirstToolWindowCommand, adicione um método ButtonHandler que invoca a caixa de diálogo **Arquivo Aberto.** Quando um arquivo é selecionado, ele reproduz o arquivo de mídia.

2. Na classe FirstToolWindowCommand, adicione uma referência privada à janela FirstToolWindow que é criada no método FindToolWindow().

    ```csharp
    private FirstToolWindow window;
    ```

3. Altere o método ShowToolWindow() para definir a janela que você definiu acima (para que o manipulador de comando ButtonHandler possa acessar o controle da janela. Aqui está o método completo ShowToolWindow().

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Adicione o método ButtonHandler. Ele cria um OpenFileDialog para que o usuário especifique o arquivo de mídia para reproduzir e, em seguida, reproduz o arquivo selecionado.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Defina a posição padrão para a janela da ferramenta

Em seguida, especifique um local padrão no IDE para a janela da ferramenta. As informações de configuração da janela da ferramenta estão no arquivo *FirstToolWindowPackage.cs.*

1. Em *FirstToolWindowPackage.cs,* <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> encontre o `FirstToolWindowPackage` atributo na classe, que passa o tipo FirstToolWindow para o construtor. Para especificar uma posição padrão, você deve adicionar mais parâmetros ao construtor seguindo o exemplo.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    O primeiro parâmetro `Style` nomeado é `Tabbed`e seu valor é , o que significa que a janela será uma guia em uma janela existente. A posição de acoplamento `Window` é especificada pelo parâmetro, neste caso, o GUID do **Solution Explorer**.

    > [!NOTE]
    > Para obter mais informações sobre os tipos <xref:EnvDTE.vsWindowType>de janelas no IDE, consulte .

## <a name="test-the-tool-window"></a>Teste a janela da ferramenta

1. Pressione **F5** para abrir uma nova instância da compilação experimental do Visual Studio.

2. No menu **Exibir,** aponte para **Outros Windows** e clique em **Primeira Janela de Ferramenta**.

    A janela da ferramenta media player deve ser aberta na mesma posição que o **Solution Explorer**. Se ele ainda aparecer na mesma posição de antes, redefinir o layout da janela **(Janela / Redefinir layout da janela**).

3. Clique no botão (ele tem o ícone **pesquisar)** na janela da ferramenta. Selecione um arquivo de som ou vídeo suportado, por exemplo, *C:\windows\media\chimes.wav*e **pressione Abrir**.

    Você deveria ouvir o som do sino.

## <a name="see-also"></a>Confira também
- [Comandos, menus e barras de ferramentas](../extensibility/internals/commands-menus-and-toolbars.md)
