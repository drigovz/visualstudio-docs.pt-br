---
title: Abrindo uma janela de ferramentas dinâmicas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702258"
---
# <a name="open-a-dynamic-tool-window"></a>Abra uma janela de ferramenta dinâmica
As janelas de ferramentas são normalmente abertas a partir de um comando em um menu ou de um atalho de teclado equivalente. Às vezes, no entanto, você pode precisar de uma janela de ferramenta que se abra sempre que um contexto específico de interface do iu se aplica e feche quando o contexto de Interface do EI não se aplica mais. Esses tipos de janelas de ferramentas são chamadas *de dinâmicas* ou *auto-visíveis*.

> [!NOTE]
> Para obter uma lista de contextos <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>de interface do ui predefinidos, consulte .

 Se você deseja abrir uma janela de ferramenta dinâmica na inicialização, e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> é possível que a criação <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> falhe, você deve implementar a interface e testar as condições de falha no método. Para que o shell saiba que você tem uma janela de ferramenta dinâmica `SupportsDynamicToolOwner` que deve ser aberta na inicialização, você deve adicionar o valor (definido para 1) ao seu registro de pacote. Esse valor não faz <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>parte do padrão, então você deve criar um atributo personalizado para adicioná-lo. Para obter mais informações sobre atributos personalizados, consulte [Usar um atributo de registro personalizado para registrar uma extensão](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Use <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> para abrir uma janela de ferramenta. A janela da ferramenta é criada conforme necessário.

> [!NOTE]
> Uma janela dinâmica de ferramenta pode ser fechada pelo usuário. Se você quiser criar um comando de menu para que o usuário possa reabrir a janela da ferramenta, o comando menu deve ser ativado no mesmo contexto de interface do usuário que abre a janela da ferramenta e desativado de outra forma.

## <a name="to-open-a-dynamic-tool-window"></a>Para abrir uma janela de ferramenta dinâmica

1. Crie um projeto VSIX chamado **DynamicToolWindow** e adicione um modelo de item de janela de ferramenta chamado *DynamicWindowPane.cs*. Para obter mais informações, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

2. No arquivo *DynamicWindowPanePackage.cs,* encontre a declaração DynamicWindowPanePackage. Adicione <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> os <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> atributos e atributos para registrar a janela da ferramenta.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Os atributos acima registram a janela da ferramenta chamada DynamicWindowPane como uma janela transitória que não é persistida quando o Visual Studio é fechado e reaberto. DynamicWindowPane é <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> aberto sempre que se aplica, e fechado de outra forma.

3. Compile o projeto e comece a depuração. A instância experimental deve aparecer. Você não deve ver a janela da ferramenta.

4. Abra um projeto na instância experimental. A janela da ferramenta deve aparecer.
