---
title: Adicionando comandos do Visual Studio a uma página inicial | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2042ef9a96eed99636ea0a2f5f09d99cd35ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699161"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Adicionando comandos do Visual Studio a uma página inicial
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao criar uma página inicial personalizada, você pode adicionar comandos do Visual Studio a ela. Este documento discute as diferentes maneiras de associar comandos do Visual Studio a objetos XAML em uma página inicial.  
  
 Para obter mais informações sobre comandos em XAML, consulte [visão geral](https://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81) de comandos  
  
## <a name="adding-commands-from-the-command-well"></a>Adicionando comandos do bem-sucommand  
 A página inicial criada na [criação de uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md) adicionou <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> os <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> namespaces e, da seguinte maneira.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Adicione outro namespace para Microsoft. VisualStudio. Shell a partir do assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Talvez seja necessário adicionar uma referência a esse assembly em seu projeto.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Você pode usar o `vscom:` alias para associar comandos do Visual Studio a controles XAML na página definindo a <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Propriedade do controle como `vscom:VSCommands.ExecuteCommand` . Em seguida, você pode definir a <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> propriedade como o nome do comando a ser executado, conforme mostrado no exemplo a seguir.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
> O `x:` alias, que se refere ao esquema XAML, é necessário no início de todos os comandos.  
  
 Você pode definir o valor da `Command` propriedade para qualquer comando que possa ser acessado na janela de **comando** . Para obter uma lista de comandos disponíveis, consulte [aliases de comando do Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Se o comando a ser adicionado exigir um parâmetro adicional, você poderá adicioná-lo ao valor da `CommandParameter` propriedade. Separe os parâmetros dos comandos usando espaços, conforme mostrado no exemplo a seguir.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Bem como chamar extensões a partir do comando  
 Você pode chamar comandos de VSPackages registrados usando a mesma sintaxe usada para chamar outros comandos do Visual Studio. Por exemplo, se um VSPackage instalado Adicionar um comando **Home Page** ao menu **Exibir** , você poderá chamar esse comando definindo `CommandParameter` como `View.HomePage` .  
  
> [!NOTE]
> Se você chamar um comando associado a um VSPackage, o pacote deverá ser carregado quando o comando for invocado.  
  
## <a name="adding-commands-from-assemblies"></a>Adicionando comandos de assemblies  
 Para chamar um comando de um assembly ou para acessar o código em um VSPackage que não está associado a um comando de menu, você deve criar um alias para o assembly e, em seguida, chamar o alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Para chamar um comando de um assembly  
  
1. Em sua solução, adicione uma referência ao assembly.  
  
2. Na parte superior do arquivo StartPage. XAML, adicione uma diretiva de namespace para o assembly, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Invoque o comando definindo a `Command` propriedade de um objeto XAML, conforme mostrado no exemplo a seguir.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Você deve copiar seu assembly e, em seguida, colá-lo no. \\ *Pasta de instalação do Visual Studio*\Common7\IDE\PrivateAssemblies\ para certificar-se de que ela está carregada antes de ser chamada.  
  
## <a name="adding-commands-with-the-dte-object"></a>Adicionando comandos com o objeto DTE  
 Você pode acessar o objeto DTE a partir de uma página inicial, tanto na marcação quanto no código.  
  
 Na marcação, você pode acessá-lo usando a sintaxe de [extensão de marcação de associação](https://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) para chamar o <xref:EnvDTE.DTE> objeto. Você pode usar essa abordagem para associar propriedades simples, como aquelas que retornam coleções, mas não é possível associar a métodos ou serviços. O exemplo a seguir mostra um <xref:System.Windows.Controls.TextBlock> controle que é associado à <xref:EnvDTE._DTE.Name%2A> propriedade e um <xref:System.Windows.Controls.ListBox> controle que enumera as <xref:EnvDTE.Window.Caption%2A> Propriedades da coleção que é retornada pela <xref:EnvDTE._DTE.Windows%2A> propriedade.  
  
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
  
 Para obter um exemplo, consulte [Walkthrough: salvar as configurações do usuário em uma página inicial](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Adicionar um controle de usuário à página inicial](../extensibility/adding-user-control-to-the-start-page.md)
