---
title: Adicionando comandos do Visual Studio a uma página inicial | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740116"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Adicionar comandos do Visual Studio a uma página inicial

Quando você cria uma página inicial personalizada, você pode adicionar comandos do Visual Studio a ela. Este documento discute as diferentes maneiras de vincular comandos do Visual Studio a objetos XAML em uma página inicial.

Para obter mais informações sobre comandos no XAML, consulte [Visão geral do Comando](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Adicionar comandos do comando bem

A página inicial criada em Criar uma <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> página [inicial personalizada](../extensibility/creating-a-custom-start-page.md) adicionou os espaços de nome e nomes, da seguinte forma.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Adicione outro namespace para Microsoft.VisualStudio.Shell a partir do conjunto *Microsoft.VisualStudio.Shell.Immutável.11.0.dll*. (Você pode precisar adicionar uma referência a esta montagem em seu projeto.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Você pode `vscom:` usar o alias para vincular os comandos do Visual <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Studio aos controles `vscom:VSCommands.ExecuteCommand`XAML na página, definindo a propriedade do controle para . Em seguida, <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> você pode definir a propriedade para o nome do comando para executar, como mostrado no exemplo a seguir.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> O `x:` alias, que se refere ao esquema XAML, é necessário no início de todos os comandos.

 Você pode definir o `Command` valor da propriedade para qualquer comando que possa ser acessado a partir da janela **comando.** Para obter uma lista de comandos disponíveis, consulte [aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Se o comando para adicionar exigir um parâmetro adicional, você `CommandParameter` pode adicioná-lo ao valor da propriedade. Separe parâmetros dos comandos usando espaços, como mostrado no exemplo a seguir.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Chamada extensões do comando bem
 Você pode chamar comandos de VSPackages registrados usando a mesma sintaxe que é usada para chamar outros comandos do Visual Studio. Por exemplo, se um VSPackage instalado adicionar um comando **Home Page** ao menu `View.HomePage` **Exibir,** você poderá chamar esse comando configurando `CommandParameter` para .

> [!NOTE]
> Se você chamar um comando associado a um VSPackage, o pacote deve ser carregado quando o comando é invocado.

## <a name="add-commands-from-assemblies"></a>Adicionar comandos de assembléias
 Para chamar um comando de um conjunto ou para acessar o código em um VSPackage que não esteja associado a um comando de menu, você deve criar um alias para o conjunto e, em seguida, chamar o alias.

### <a name="to-call-a-command-from-an-assembly"></a>Para chamar um comando de uma assembléia

1. Na sua solução, adicione uma referência à montagem.

2. Na parte superior do arquivo *StartPage.xaml,* adicione uma diretiva namespace para o conjunto, conforme mostrado no exemplo a seguir.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Invoque o `Command` comando definindo a propriedade de um objeto XAML, como mostrado no exemplo a seguir.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Você deve copiar sua montagem e depois colá-la em *.. \\{Pasta de instalação do Visual Studio}\Common7\IDE\PrivateAssemblies\* para ter certeza de que está carregada antes de ser chamada.

## <a name="add-commands-with-the-dte-object"></a>Adicionar comandos com o objeto DTE
 Você pode acessar o objeto DTE a partir de uma Página inicial, tanto na marcação quanto no código.

 Na marcação, você pode acessá-lo usando a <xref:EnvDTE.DTE> sintaxe [de extensão de marcação vinculante](/dotnet/framework/wpf/advanced/binding-markup-extension) para chamar o objeto. Você pode usar essa abordagem para vincular-se a propriedades simples, como aquelas que retornam coleções, mas você não pode se vincular a métodos ou serviços. O exemplo a <xref:System.Windows.Controls.TextBlock> seguir mostra um <xref:EnvDTE._DTE.Name%2A> controle que <xref:System.Windows.Controls.ListBox> se liga ao <xref:EnvDTE.Window.Caption%2A> imóvel, e um controle que <xref:EnvDTE._DTE.Windows%2A> enumera as propriedades do acervo que é devolvido pelo imóvel.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Por exemplo, consulte [Passo a Passo: Salvando as configurações](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)do usuário em uma página inicial .

## <a name="see-also"></a>Confira também

- [Adicionando controle de usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md)
