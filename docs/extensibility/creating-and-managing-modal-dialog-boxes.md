---
title: Criação e gerenciamento de caixas de diálogo modal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739488"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Criar e gerenciar caixas de diálogo modal
Quando você criar uma caixa de diálogo modal dentro do Visual Studio, você deve certificar-se de que a janela pai da caixa de diálogo está desativada enquanto a caixa de diálogo é exibida e, em seguida, reative a janela pai depois que a caixa de diálogo estiver fechada. Se você não fizer isso, você pode receber o erro: o *Microsoft Visual Studio não pode ser desligado porque uma caixa de diálogo modal está ativa. Feche a caixa de diálogo ativa e tente novamente.*

Há duas maneiras de fazer isso. A maneira recomendada, se você tiver uma caixa de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>diálogo WPF, é deriva-la e, em seguida, chamar <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> para exibir a caixa de diálogo. Se você fizer isso, você não precisa gerenciar o estado modal da janela dos pais.

Se a caixa de diálogo não for WPF, ou por <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>algum outro motivo que você não possa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> derivar sua classe de caixa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> de diálogo, então você deve obter o pai da caixa de diálogo ligando e gerenciando o estado modal você mesmo, chamando o método com um parâmetro de 0 (falso) antes de exibir a caixa de diálogo e chamar o método novamente com um parâmetro de 1 (verdadeiro) após o fechamento da caixa de diálogo.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Criar uma caixa de diálogo derivada do DialogWindow

1. Crie um projeto VSIX chamado **OpenDialogTest** e adicione um comando de menu chamado **OpenDialog**. Para obter mais informações sobre como fazer isso, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Para usar <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> a classe, você deve adicionar referências às seguintes assembléias (na guia 'Quadro da caixa de diálogo **Adicionar** referência):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. Em *OpenDialog.cs,* adicione `using` a seguinte declaração:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Declare uma `TestDialogWindow` classe chamada <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>que deriva de:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Para poder minimizar e maximizar a caixa <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> de diálogo, definir e verdadeiro:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. No `OpenDialog.ShowMessageBox` método, substitua o código existente pelo seguinte:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Criar e executar o aplicativo. A instância experimental do Visual Studio deve aparecer. No menu **Ferramentas** da instância experimental, você deve ver um comando chamado **Invocar OpenDialog**. Quando você clica neste comando, você deve ver a janela de diálogo. Você deve ser capaz de minimizar e maximizar a janela.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Criar e gerenciar uma caixa de diálogo não derivada do DialogWindow

1. Para este procedimento, você pode usar a solução **OpenDialogTest** criada no procedimento anterior, com as mesmas referências de montagem.

2. Adicione as `using` seguintes declarações:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Crie uma `TestDialogWindow2` classe chamada <xref:System.Windows.Window>que deriva de:

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Adicione uma referência <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>privada a:

    ```
    private IVsUIShell shell;
    ```

5. Adicionar um construtor que define <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>a referência a:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. No `OpenDialog.ShowMessageBox` método, substitua o código existente pelo seguinte:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Criar e executar o aplicativo. No menu **Ferramentas,** você deve ver um comando chamado **Invocar OpenDialog**. Quando você clica neste comando, você deve ver a janela de diálogo.
