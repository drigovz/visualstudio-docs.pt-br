---
title: Comportamento novo ou alterado com adaptadores do editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194174"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportamento novo ou alterado com adaptadores do Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você estiver atualizando o código que foi escrito em relação às versões anteriores do Visual Studio Core editor e planeja usar os adaptadores do editor (ou shims) em vez de usar a nova API, você deve estar ciente das diferenças a seguir no comportamento dos adaptadores do editor em relação ao editor de núcleo anterior.  
  
## <a name="features"></a>Recursos  
  
#### <a name="using-setsite"></a>Usando SetSite ()  
 Você deve chamar <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> ao Cocriar buffers de texto, exibições de texto e janelas de código antes de executar qualquer outra operação neles. No entanto, isso não será necessário se você usar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> para criá-los, pois os próprios métodos Create () desse serviço chamam <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hospedando IVsCodeWindow e IVsTextView em seu próprio conteúdo  
 Você pode hospedar tanto o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> quanto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> o em seu próprio conteúdo usando o modo Win32 ou o modo WPF. No entanto, você deve ter em mente que há algumas diferenças nos dois modos.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Usando as versões Win32 e WPF do IVsCodeWindow  
 A janela de código do editor é derivada de <xref:Microsoft.VisualStudio.Shell.WindowPane> , que implementa a interface Win32 mais antiga, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> bem como a nova interface do WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> . Você pode usar o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> método para criar um ambiente de hospedagem baseado em HWND ou o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> método para criar um ambiente de hospedagem do WPF. O editor subjacente sempre usa o WPF, mas você pode criar o tipo de painel de janela que atenda aos seus requisitos de hospedagem se você estiver inserindo esse painel de janela diretamente em seu próprio conteúdo.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Usando as versões Win32 e WPF do IVsTextView  
 Você pode definir um modo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Win32 ou o modo WPF.  
  
 Quando uma fábrica de editor cria uma exibição de texto, por padrão ela é hospedada dentro de um HWND e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> retorna um HWND. Você não deve usar esse modo para inserir o editor dentro de um controle WPF.  
  
 Para definir uma exibição de texto para o modo WPF, você deve chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> e passar <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> como um dos sinalizadores de inicialização no `InitView` parâmetro. Você pode obter o <xref:System.Windows.FrameworkElement> chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 O modo WPF difere do modo Win32 de duas maneiras. Primeiro, a exibição de texto pode ser hospedada em um contexto do WPF. Você pode acessar o painel do WPF convertendo o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> e chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . Segundo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> ainda retorna um HWND, mas esse HWND só pode ser usado para verificar sua posição e definir o foco nele. Você não deve usar esse HWND para responder a uma mensagem de WM_PAINT, porque ele não afetará a forma como o editor pinta a janela. Esse HWND está presente apenas para facilitar a transição para o novo código do editor por meio dos adaptadores. É altamente recomendável que você não use `VIF_NO_HWND_SUPPORT` se seu componente exigir que um HWND funcione, devido às limitações no HWND retornado de `GetWindowHandle` enquanto está nesse modo.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passando matrizes como parâmetros em código nativo  
 Há muitos métodos na API do editor herdado que têm parâmetros que incluem uma matriz e sua contagem. São exemplos:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Se você estiver chamando esses métodos no código nativo, deverá passar apenas um elemento por vez. Se você passar mais de um elemento, a chamada será rejeitada, devido a problemas com a implementação de interoperabilidade primária.  
  
 O problema é mais complexo com métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Sempre que esse método é chamado, ele limpa a lista anterior de tipos de marcador ignorados, portanto, não é possível simplesmente chamar esse método três vezes com três tipos de marcador diferentes. A única solução é chamar esse método somente no código gerenciado.  
  
#### <a name="threading"></a>Threading  
 Você sempre deve chamar o adaptador de buffer do thread da interface do usuário. O adaptador de buffer é um objeto gerenciado, o que significa que chamá-lo do código gerenciado irá ignorar o marshaling COM e sua chamada não será automaticamente empacotada para o thread da interface do usuário.  Se você estiver chamando o adaptador de buffer de um thread em segundo plano, deverá usar o <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou um método semelhante.  
  
#### <a name="lockbuffer-methods"></a>Métodos LockBuffer  
 Todos os métodos LockBuffer () foram preteridos. São exemplos:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Eventos de confirmação  
 Não há suporte para eventos Commit. Chamar um método que aconselha esses eventos faz com que o método retorne um código de falha.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 O <xref:EnvDTE.TextEditorEvents> não é mais acionado na confirmação (). Em vez disso, eles são acionados em cada alteração de texto.  
  
#### <a name="text-markers"></a>Marcadores de texto  
 Você deve chamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objetos quando removê-los. Nas versões anteriores, você precisava apenas liberar os marcadores.  
  
#### <a name="line-numbers"></a>Números de linha  
 Para uma variedade de métodos no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> e no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> , os números de linha correspondem aos números de linha de buffer subjacentes, e não a números de linha que fator em estrutura de tópicos e quebra automática de palavras, como no Visual Studio 2008.  
  
 Os métodos afetados incluem o seguinte (a lista não é exaustiva):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Estrutura de tópicos  
 Os clientes do verão <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> apenas as regiões de estrutura de tópicos que foram adicionadas usando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> ou o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Eles não verão regiões ad hoc, porque não são adicionados por meio dos adaptadores do editor. Da mesma forma, esses clientes não verão regiões de estrutura de tópicos adicionadas por linguagens (incluindo C# e C++) que estão usando o novo código do editor em vez dos adaptadores do editor.  
  
#### <a name="line-heights"></a>Alturas de linha  
 No novo editor, as linhas de texto podem ter alturas diferentes, dependendo do tamanho da fonte e das possíveis transformações de linha que podem mover a linha em relação a outras linhas. A altura da linha retornada por métodos como <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> é a altura de uma linha usando o tamanho da fonte padrão sem transformações de linha aplicadas. Essa altura pode ou não refletir a altura real de uma linha na exibição.  
  
#### <a name="eventing-and-undo"></a>Eventos e desfazer  
 No novo editor, a exibição continua a executar operações como renderizar e gerar eventos continuamente, mesmo quando um cluster de desfazer está aberto. Esse comportamento é diferente dos modos de exibição herdados, que não realizaram essas operações até o fechamento do cluster de desfazer.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> método falhará se você passar uma classe que não implementa um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Não há mais suporte para os pop-ups personalizados de proprietário do Win32.  
  
#### <a name="smarttags"></a>SmartTag  
 Não há suporte de adaptador para marcas inteligentes criadas com <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> interfaces,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>ESTABELECIDA  
 <xref:EnvDTE80.IncrementalSearch> Não está implementado.  
  
## <a name="unimplemented-methods"></a>Métodos não implementados  
 Alguns métodos não foram implementados no adaptador de buffer de texto, no adaptador de exibição de texto e no adaptador da camada de texto.  
  
|Interface|Não implementado|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Não está implementado.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> é implementado nos adaptadores, mas ignorado pela interface do usuário da estrutura de tópicos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> é implementado nos adaptadores, mas ignorado pela interface do usuário da estrutura de tópicos.|
