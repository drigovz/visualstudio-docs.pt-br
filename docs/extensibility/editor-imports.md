---
title: Importações do Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712006"
---
# <a name="editor-imports"></a>Importações do editor
Você pode importar uma série de serviços de editor, fábricas e corretores que fornecem sua extensão com diferentes tipos de acesso ao editor principal. Por exemplo, você <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> pode importar o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> para fornecer-lhe um para um determinado tipo de conteúdo. (Este navegador permite que você execute diferentes tipos de pesquisas em um buffer de texto.)

 Para usar uma importação de editor, você a importa como um campo ou propriedade de uma classe que exporta uma parte componente do Componente Quadro de Extensibilidade Gerenciada.

> [!NOTE]
> Para obter mais informações sobre o Quadro de Extensibilidade Gerenciada, consulte [Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada).](/dotnet/framework/mef/index)

## <a name="import-syntax"></a>Sintaxe de importação
 O exemplo a seguir mostra como importar o serviço de fábrica de opções de editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Se você quiser importar o serviço como um campo e `null` não como uma propriedade, você deve configurá-lo na declaração para evitar os avisos do compilador sobre não atribuir a uma variável:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Para obter mais exemplos de utilização de importações, consulte os seguintes passos a passo:

- [Passo a passo: Crie um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Passo a passo: Personalize a visualização de texto](../extensibility/walkthrough-customizing-the-text-view.md)

- [Passo a passo: Texto de destaque](../extensibility/walkthrough-highlighting-text.md)

- [Passo a passo: Exibir dicas de ferramentas do QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Passo a passo: Ajuda de assinatura de exibição](../extensibility/walkthrough-displaying-signature-help.md)

- [Passo a passo: exibir preenchimento de declaração](../extensibility/walkthrough-displaying-statement-completion.md)

- [Passo a passo: Exibir sugestões de lâmpadas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importar o provedor de serviços
 Você também pode <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> importar um (encontrado no conjunto Microsoft.VisualStudio.Shell.Immutable.10.0) da mesma forma para ter acesso aos serviços do Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Consulte [passo a passo: acesse o objeto DTE a partir de uma extensão de editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) para obter mais informações.

## <a name="services"></a>Serviços
 Os serviços de editor são geralmente entidades únicas que fornecem um serviço e são compartilhados em vários componentes.

|Importar|Fornece o|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|A relação entre extensões de arquivos e <xref:Microsoft.VisualStudio.Utilities.IContentType> objetos.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|A coleção dos objetos <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Objetos.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Muitos objetos adaptadores de editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Um <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> objeto para uma determinada exibição de texto.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Um <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Um <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Uma <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> das diferenças.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Uma <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> das diferenças.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> ou <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>um.|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> para um <xref:Microsoft.VisualStudio.Text.ITextBuffer> conjunto de objetos.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para <xref:Microsoft.VisualStudio.Text.ITextBuffer>um.|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um.|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Um <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantém a <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> coleção de objetos.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> para um buffer de texto.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> para uma exibição de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|O <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> para o escopo especificado.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> para uma exibição de texto.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Um <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Obtém o recuo <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> automático através dos objetos.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gerencia o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> para <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>um .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Gera texto formatado por RTF a partir de um conjunto de intervalos de instantâneos.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> para formatação de linhas de texto em uma exibição.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Um <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> objeto <xref:Microsoft.VisualStudio.Text.Editor.ITextView>para um.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Pesquisa um instantâneo de texto.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> por <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>um by .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Um <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> para uma exibição de texto.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Um conjunto padrão de glifos.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Um <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> para <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Rastreia o manuseio do teclado.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Objetos padrão. <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantém a relação entre <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> buffers de texto e objetos.|

## <a name="other-imports"></a>Outras importações
 Fábricas de provedores e corretores são geralmente entidades que podem ter múltiplas instâncias em vários componentes.

|Importar|Fornece o|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> de <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>tipo ) para o buffer dado.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Um marcador de texto <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> tagger (a do tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Um <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> por <xref:Microsoft.VisualStudio.Text.Editor.ITextView>um dado.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Um <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Um <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Um <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Confira também
- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
