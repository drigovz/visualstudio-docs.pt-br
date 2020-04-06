---
title: 'Passo a passo: Texto de destaque | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697396"
---
# <a name="walkthrough-highlight-text"></a>Passo a passo: Texto de destaque
Você pode adicionar diferentes efeitos visuais ao editor criando componentes MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada). Este passo a passo mostra como destacar cada ocorrência da palavra atual em um arquivo de texto. Se uma palavra ocorre mais de uma vez em um arquivo de texto, e você posiciona o cuidador em uma ocorrência, cada ocorrência é destacada.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Crie um projeto MEF

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `HighlightWordTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

## <a name="define-a-textmarkertag"></a>Defina um TextMarkerTag
 O primeiro passo para destacar o <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> texto é subclasse e definir sua aparência.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Para definir um TextMarkerTag e um MarkerFormatDefinition

1. Adicione um arquivo de classe e nomeie-o **HighlightWordTag**.

2. Adicione as seguintes referências:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.visualStudio.text.Logic

    4. Microsoft.visualStudio.text.ui

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. Apresentação.Core

    8. Apresentação.Framework

3. Importe os seguintes namespaces.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Crie uma classe que <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> herde `HighlightWordTag`e nomeie-a.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Crie uma segunda classe <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>que herde `HighlightWordFormatDefinition`, e nomeá-la . Para usar essa definição de formato para sua tag, você deve exportá-la com os seguintes atributos:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: as tags usam isso para referenciar este formato

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: isso faz com que o formato apareça na ui

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. No construtor de HighlightWordFormatDefinition, defina seu nome de exibição e aparência. A propriedade Background define a cor de preenchimento, enquanto a propriedade Foreground define a cor da borda.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. No construtor de HighlightWordTag, passe no nome da definição de formato que você criou.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementar um ITagger
 O próximo passo é <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementar a interface. Esta interface atribui, a um determinado buffer de texto, tags que fornecem destaque de texto e outros efeitos visuais.

### <a name="to-implement-a-tagger"></a>Para implementar um tagger

1. Crie uma classe <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> que `HighlightWordTag`implemente o `HighlightWordTagger`tipo e nomeie-o .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Adicione os seguintes campos e propriedades privadas à classe:

    - Uma <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, que corresponde à exibição de texto atual.

    - Um <xref:Microsoft.VisualStudio.Text.ITextBuffer>, que corresponde ao buffer de texto que está por trás da exibição do texto.

    - Um <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, que é usado para encontrar texto.

    - Um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, que tem métodos para navegar dentro de períodos de texto.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, que contém o conjunto de palavras para destacar.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, que corresponde à palavra atual.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, que corresponde à posição atual do cuidador.

    - Um objeto de bloqueio.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Adicione um construtor que inicialize as propriedades <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> listadas anteriormente e adicione e os manipuladores de eventos.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Os manipuladores de `UpdateAtCaretPosition` eventos chamam o método.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Você também deve `TagsChanged` adicionar um evento que é chamado pelo método de atualização.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. O `UpdateAtCaretPosition()` método encontra cada palavra no buffer de texto que é idêntica à palavra <xref:Microsoft.VisualStudio.Text.SnapshotSpan> onde o cursor está posicionado e constrói uma lista de objetos que correspondem às ocorrências da palavra. Em seguida, chama `SynchronousUpdate` `TagsChanged` , o que levanta o evento.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. O `SynchronousUpdate` executa uma atualização `WordSpans` síncrona sobre as propriedades e `CurrentWord` levanta o `TagsChanged` evento.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Você deve <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> implementar o método. Este método pega <xref:Microsoft.VisualStudio.Text.SnapshotSpan> uma coleção de objetos e retorna uma enumeração de períodos de etiqueta.

     Em C#, implemente este método como um iterador de rendimento, que permite uma avaliação preguiçosa (ou seja, avaliação do conjunto somente quando itens individuais são acessados) das tags. No Visual Basic, adicione as tags a uma lista e retorne a lista.

     Aqui o método <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> retorna um objeto <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>que tem um "azul", que fornece um fundo azul.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Criar um provedor tagger
 Para criar seu tagger, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>você deve implementar um . Esta classe é uma parte componente MEF, então você deve definir os atributos corretos para que esta extensão seja reconhecida.

> [!NOTE]
> Para obter mais informações sobre o MEF, consulte [Quadro de Extensibilidade Gerenciada (MEF).](/dotnet/framework/mef/index)

### <a name="to-create-a-tagger-provider"></a>Para criar um provedor de tagger

1. Crie uma `HighlightWordTaggerProvider` classe nomeada <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>que implemente <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , e exporte-a com um de "texto" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Você deve importar dois <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> serviços <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>de editor, o e o , para instanciar o tagger.

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementar <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> o método para `HighlightWordTagger`retornar uma instância de .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Construa e teste o código
 Para testar esse código, crie a solução HighlightWordTest e execute-o na instância experimental.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Para construir e testar a solução HighlightWordTest

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto no qual as palavras são repetidas, por exemplo, "olá olá".

4. Posicione o cursor em uma das ocorrências de "olá". Todas as ocorrências devem ser destacadas em azul.

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
