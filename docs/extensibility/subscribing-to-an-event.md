---
title: Inscrição para um Evento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699680"
---
# <a name="subscribing-to-an-event"></a>Assinando um evento
Este passo a passo explica como criar uma janela de ferramenta que responda a eventos em uma tabela de documentos em execução (RDT). Uma janela de ferramenta hospeda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>um controle de usuário que implementa . O <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta a interface aos eventos.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>Subscrevendo-se à RDT Events

#### <a name="to-create-an-extension-with-a-tool-window"></a>Para criar uma extensão com uma janela de ferramenta

1. Crie um projeto chamado **RDTExplorer** usando o modelo VSIX e adicione um modelo de item de janela de ferramenta personalizado chamado **RDTExplorerWindow**.

     Para obter mais informações sobre como criar uma extensão com uma janela de ferramenta, consulte [Criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>Para se inscrever em eventos RDT

1. Abra o arquivo RDTExplorerWindowControl.xaml e `button1`exclua o botão chamado . Adicione <xref:System.Windows.Forms.ListBox> um controle e aceite o nome padrão. O elemento Grade deve ser assim:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Abra o arquivo RDTExplorerWindow.cs na exibição de código. Adicione as seguintes diretivas usando o início do arquivo.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Modifique `RDTExplorerWindow` a classe para que, além <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> de derivada da <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> classe, implemente a interface.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>.

    - Implemente a interface. Coloque o cursor no nome IVsRunningDocTableEvents. Você deve ver uma lâmpada na margem esquerda. Clique na seta Para baixo à direita da lâmpada e selecione **Implemente interface**.

5. Em cada método na interface, `throw new NotImplementedException();` substitua a linha por isso:

    ```csharp
    return VSConstants.S_OK;
    ```

6. Adicione um campo de cookies à classe RDTExplorerWindow.

    ```csharp
    private uint rdtCookie;
    ```

     Isso contém o cookie que <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> é devolvido pelo método.

7. Substituir o método Initialize() do RDTExplorerWindow para registrar eventos RDT. Você deve sempre obter serviços no método Initialize() do ToolWindowPane, não no construtor.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     O <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> serviço é chamado <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> para obter uma interface. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> método conecta eventos RDT a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>um objeto que implementa, neste caso, um objeto RDTExplorer.

8. Atualize o método Descarte() do RDTExplorerWindow.

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

     O <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> método exclui a `RDTExplorer` conexão entre a notificação de evento RDT.

9. Adicione a seguinte linha ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> corpo do `return` manipulador, pouco antes da declaração.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. Adicione uma linha semelhante ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> corpo do manipulador e a outros eventos que você deseja ver na caixa de lista.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Compile o projeto e comece a depuração. A instância experimental do Visual Studio é exibida.

12. Abra o **RDTExplorerWindow** **(Ver / Outros Windows / RDTExplorerWindow**).

     A janela **RDTExplorerWindow** é aberta com uma lista de eventos vazia.

13. Abra ou crie uma solução.

     À `OnBeforeLastDocument` `OnAfterFirstDocument` medida que os eventos são disparados, a notificação de cada evento aparece na lista de eventos.
