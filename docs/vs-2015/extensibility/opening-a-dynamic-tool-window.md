---
title: Abrindo uma janela de ferramentas dinâmicas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838574"
---
# <a name="opening-a-dynamic-tool-window"></a>Abrindo uma janela de ferramentas dinâmica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As janelas de ferramentas normalmente são abertas a partir de um comando em um menu ou um atalho de teclado equivalente. Às vezes, no entanto, você pode precisar de uma janela de ferramenta que é aberta sempre que um contexto de interface do usuário específico se aplica e fecha quando o contexto da interface do usuário não se aplica mais. Janelas de ferramentas como essas são chamadas *dinâmicas* ou *visíveis automaticamente*.  
  
> [!NOTE]
> Para obter uma lista de contextos predefinidos da interface do usuário, consulte <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> . Em  
  
 Se você quiser abrir uma janela de ferramenta dinâmica na inicialização e for possível que a criação falhe, você deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interface e testar as condições de falha no <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> método. Para que o Shell saiba que você tem uma janela de ferramenta dinâmica que deve ser aberta na inicialização, você deve adicionar o `SupportsDynamicToolOwner` valor (definido como 1) ao seu registro de pacote. Esse valor não faz parte do padrão <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , portanto, você deve criar um atributo personalizado para adicioná-lo. Para obter mais informações sobre atributos personalizados, consulte [usando um atributo de registro personalizado para registrar uma extensão](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir uma janela de ferramentas. A janela de ferramentas é criada conforme necessário.  
  
> [!NOTE]
> Uma janela de ferramenta dinâmica pode ser fechada pelo usuário. Se você quiser criar um comando de menu para que o usuário possa reabrir a janela de ferramentas, o comando de menu deverá ser habilitado no mesmo contexto de interface do usuário que abre a janela de ferramentas e desabilitado de outra forma.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Para abrir uma janela de ferramentas dinâmicas  
  
1. Crie um projeto VSIX chamado **DynamicToolWindow** e adicione um modelo de item da janela de ferramentas chamado **DynamicWindowPane.cs**. Para obter mais informações, consulte [criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2. No arquivo DynamicWindowPanePackage.cs, localize a declaração DynamicWindowPanePackage. Adicione os <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atributos e T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute para registrar a janela de ferramentas.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Isso registra a janela de ferramentas chamada DynamicWindowPane como uma janela transitória que não é persistida quando o Visual Studio é fechado e reaberto. DynamicWindowPane é aberto sempre que <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> se aplica e fechado caso contrário.  
  
3. Compile o projeto e comece a depuração. A instância experimental deve aparecer. Você não verá a janela de ferramentas.  
  
4. Abra um projeto na instância experimental. A janela de ferramentas deve aparecer.
