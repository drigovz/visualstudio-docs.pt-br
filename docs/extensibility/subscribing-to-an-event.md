---
title: Inscrevendo-se em um evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647924"
---
# <a name="subscribing-to-an-event"></a>Assinando um evento
Este tutorial explica como criar uma janela de ferramentas que responde a eventos em uma tabela de documentos em execução (RDT). Uma janela de ferramentas hospeda um controle de usuário que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>. O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> conecta a interface aos eventos.

## <a name="prerequisites"></a>Prerequisites
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Inscrevendo-se em eventos RDT

#### <a name="to-create-an-extension-with-a-tool-window"></a>Para criar uma extensão com uma janela de ferramentas

1. Crie um projeto chamado **RDTExplorer** usando o modelo VSIX e adicione um modelo de item de janela de ferramenta personalizada chamado **RDTExplorerWindow**.

     Para obter mais informações sobre como criar uma extensão com uma janela de ferramentas, consulte [criando uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Para assinar eventos do RDT

1. Abra o arquivo RDTExplorerWindowControl. XAML e exclua o botão chamado `button1`. Adicione um controle de <xref:System.Windows.Forms.ListBox> e aceite o nome padrão. O elemento Grid deve ser assim:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Abra o arquivo RDTExplorerWindow.cs na exibição de código. Adicione as seguintes diretivas using ao início do arquivo.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifique a classe `RDTExplorerWindow` para que, além de derivar da classe <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, ela implemente a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implemente a interface. Coloque o cursor no nome do IVsRunningDocTableEvents. Você deverá ver uma lâmpada na margem esquerda. Clique na seta para baixo à direita da lâmpada e selecione **implementar interface**.

5. Em cada método na interface, substitua a linha `throw new NotImplementedException();` por:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Adicione um campo de cookie à classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Isso mantém o cookie retornado pelo método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>.

7. Substitua o método Initialize () do RDTExplorerWindow para se registrar para eventos RDT. Você sempre deve obter serviços no método Initialize () do ToolWindowPane, não no construtor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     O serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> é chamado para obter uma interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable>. O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> conecta eventos RDT a um objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>, nesse caso, um objeto RDTExplorer.

8. Atualize o método Dispose () do RDTExplorerWindow.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> exclui a conexão entre `RDTExplorer` e a notificação de eventos RDT.

9. Adicione a seguinte linha ao corpo do manipulador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>, logo antes da instrução `return`.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Adicione uma linha semelhante ao corpo do manipulador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> e a outros eventos que você deseja ver na caixa de listagem.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compile o projeto e comece a depuração. A instância experimental do Visual Studio é exibida.

12. Abra o **RDTExplorerWindow** (**View/Other Windows/RDTExplorerWindow**).

     A janela **RDTExplorerWindow** é aberta com uma lista de eventos vazia.

13. Abra ou crie uma solução.

     Como `OnBeforeLastDocument` e os eventos de `OnAfterFirstDocument` são acionados, a notificação de cada evento aparece na lista de eventos.
