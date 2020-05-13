---
title: Criando uma janela de ferramentas em várias instâncias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739616"
---
# <a name="create-a-multi-instance-tool-window"></a>Crie uma janela de ferramenta de várias instâncias
Você pode programar uma janela de ferramenta para que várias instâncias dela possam ser abertas simultaneamente. Por padrão, as janelas de ferramentas podem ter apenas uma instância aberta.

Quando você usa uma janela de ferramenta de várias instâncias, você pode mostrar várias fontes de informação relacionadas ao mesmo tempo. Por exemplo, você pode colocar <xref:System.Windows.Forms.TextBox> um controle de várias linhas em uma janela de ferramenta de várias instâncias para que vários trechos de código estejam simultaneamente disponíveis durante uma sessão de programação. Além disso, por exemplo, <xref:System.Windows.Forms.DataGrid> você pode colocar um controle e uma caixa de lista suspensa em uma janela de ferramenta de várias instâncias para que várias fontes de dados em tempo real possam ser rastreadas simultaneamente.

## <a name="create-a-basic-single-instance-tool-window"></a>Criar uma janela de ferramenta básica (instância única)

1. Crie um projeto chamado **MultiInstanceToolWindow** usando o modelo VSIX e adicione um modelo personalizado de item de janela de ferramenta chamado **MIToolWindow**.

    > [!NOTE]
    > Para obter mais informações sobre como criar uma extensão com uma janela de ferramenta, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Faça uma janela de ferramenta multi-instância

1. Abra *MIToolWindowPackage.cs* o arquivo MIToolWindowPackage.cs `ProvideToolWindow` e encontre o atributo. e `MultiInstances=true` o parâmetro, como mostrado no exemplo a seguir:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. No arquivo *MIToolWindowCommand.cs,* `ShowToolWindos()` encontre o método. Neste método, chame <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> o método `create` e `false` defina seu sinalizador para que ele itera `id` através das instâncias de janela de ferramenta existentes até que um disponível seja encontrado.

3. Para criar uma instância de <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> janela de `id` ferramenta, chame `create` o `true`método e defina-o como um valor disponível e sua bandeira para .

    Por padrão, o `id` valor do <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> parâmetro `0`do método é . Esse valor faz uma janela de ferramenta de instância única. Para que mais de uma instância seja hospedada, `id`cada instância deve ter sua própria única .

4. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> no objeto que <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> é devolvido pela propriedade da instância da janela da ferramenta.

5. Por padrão, `ShowToolWindow` o método criado pelo modelo de item da janela da ferramenta cria uma janela de ferramenta de instância única. O exemplo a seguir `ShowToolWindow` mostra como modificar o método para criar várias instâncias.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
