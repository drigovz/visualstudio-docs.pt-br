---
title: 'Passo a passo: Exibindo sugestões de lâmpadas | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697480"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Passo a passo: Exibir sugestões de lâmpadas
As lâmpadas são ícones do editor do Visual Studio que se expandem para exibir um conjunto de ações, por exemplo, correções para problemas identificados pelos analisadores de código incorporados ou refatoração de código.

 Nos editores Visual C# e Visual Basic, você também pode usar a Plataforma de Compilador .NET ("Roslyn") para escrever e empacotar seus próprios analisadores de código com ações que exibem lâmpadas automaticamente. Para obter mais informações, consulte:

- [Como: Escrever um diagnóstico C# e corrigir código](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Como: Escrever um diagnóstico e correção de código visual básico](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Outros idiomas, como c++ também fornecem lâmpadas para algumas ações rápidas, como, uma sugestão para criar uma implementação stub dessa função.

  Aqui está como uma lâmpada se parece. Em um projeto Visual Basic ou Visual C#, um squiggle vermelho aparece sob um nome variável quando é inválido. Se você passar o mouse sobre o identificador inválido, uma lâmpada aparecerá perto do cursor.

  ![Lâmpada](../extensibility/media/lightbulb.png "Lâmpada")

  Se você clicar na seta para baixo pela lâmpada, um conjunto de ações sugeridas será exibido, juntamente com uma visualização da ação selecionada. Neste caso, ele mostra as alterações que são feitas no seu código se você executar a ação.

  ![visualização de lâmpada](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  Você pode usar lâmpadas para fornecer suas próprias ações sugeridas. Por exemplo, você pode fornecer ações para mover chaves de abertura para uma nova linha ou movê-las para o final da linha anterior. O passo a passo a seguir mostra como criar uma lâmpada que aparece na palavra atual e tem duas ações sugeridas: **Converter para maiúscula** e **Converter em minúscula**.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Criar um projeto MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada)

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `LightBulbTest`solução.

2. Adicione um modelo de item **do Editor Classifier** ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

4. Adicione a seguinte referência ao projeto e `False`defina Copy **Local** para:

     *Microsoft.VisualStudio.Language.Intellisense*

5. Adicione um novo arquivo de classe e nomeie-o **LightBulbTest**.

6. Adicione o seguinte usando as orientações:

    ```csharp
    using System;
    using System.Linq;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    using Microsoft.VisualStudio.Language.Intellisense;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Utilities;
    using System.ComponentModel.Composition;
    using System.Threading;

    ```

## <a name="implement-the-light-bulb-source-provider"></a>Implementar o provedor de fonte de lâmpada

1. No arquivo de classe *LightBulbTest.cs,* exclua a classe LightBulbTest. Adicionar uma classe chamada **TestSuggestedActionsSourceProvider** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportá-lo com um Nome de <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Teste Ações **Sugeridas** e um de "texto".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Dentro da classe do <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> provedor de origem, importe-o e adicione-o como uma propriedade.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> o método <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> para devolver um objeto. A fonte é discutida na próxima seção.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementar o ISuggestedActionSource
 A fonte de ação sugerida é responsável por coletar o conjunto de ações sugeridas e adicioná-las no contexto certo. Neste caso, o contexto é a palavra atual e as ações sugeridas são **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, que é discutida na seção a seguir.

1. Adicionar uma classe **TestSuggestedActionsSource** que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Adicione campos privados e somente leitura para o provedor de origem de ação sugerido, o buffer de texto e a exibição de texto.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Adicione um construtor que define os campos privados.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Adicione um método privado que retorna a palavra que está atualmente sob o cursor. O método a seguir analisa a localização atual do cursor e pergunta ao navegador da estrutura de texto a extensão da palavra. Se o cursor estiver em <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> uma palavra, o é devolvido no parâmetro out; caso contrário, `out` o `null` parâmetro é `false`e o método retorna.

    ```csharp
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)
    {
        ITextCaret caret = m_textView.Caret;
        SnapshotPoint point;

        if (caret.Position.BufferPosition > 0)
        {
            point = caret.Position.BufferPosition - 1;
        }
        else
        {
            wordExtent = default(TextExtent);
            return false;
        }

        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);

        wordExtent = navigator.GetExtentOfWord(point);
        return true;
    }
    ```

5. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> . O editor chama este método para saber se deve exibir a lâmpada. Esta chamada é feita frequentemente, por exemplo, sempre que o cursor se move de uma linha para outra, ou quando o mouse paira sobre um erro squiggle. É assíncrono para permitir que outras operações de iu-ions continuem enquanto este método está funcionando. Na maioria dos casos, esse método precisa realizar alguns análises e análises da linha atual, de modo que o processamento pode levar algum tempo.

     Nesta implementação, ele recebe assíncronamente <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> e determina se a extensão é significativa, como em, se tem algum texto além do espaço em branco.

    ```csharp
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        return Task.Factory.StartNew(() =>
        {
            TextExtent extent;
            if (TryGetWordUnderCaret(out extent))
            {
                // don't display the action if the extent has whitespace
                return extent.IsSignificant;
              }
            return false;
        });
    }
    ```

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> o método, que <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> retorna uma <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> matriz de objetos que contêm os diferentes objetos. Este método é chamado quando a lâmpada é expandida.

    > [!WARNING]
    > Você deve ter certeza de `HasSuggestedActionsAsync()` `GetSuggestedActions()` que as implementações são consistentes; ou seja, `HasSuggestedActionsAsync()` `true`se `GetSuggestedActions()` retornar, então deve ter algumas ações para exibir. Em muitos `HasSuggestedActionsAsync()` casos, é `GetSuggestedActions()`chamado pouco antes, mas nem sempre é assim. Por exemplo, se o usuário invocar as ações da lâmpada pressionando `GetSuggestedActions()` **(CTRL+** .) é chamado apenas.

    ```csharp
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)
    {
        TextExtent extent;
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)
        {
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };
        }
        return Enumerable.Empty<SuggestedActionSet>();
    }
    ```

7. Defina `SuggestedActionsChanged` um evento.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Para concluir a implementação, `Dispose()` adicione `TryGetTelemetryId()` implementações para os métodos. Você não quer fazer telemetria, então `false` é só voltar `Empty`e definir o GUID para .

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample provider and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

## <a name="implement-light-bulb-actions"></a>Implementar ações de lâmpadas

1. No projeto, adicione uma referência ao *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* e defina **Copy Local** para `False`.

2. Crie duas classes, `UpperCaseSuggestedAction` a primeira `LowerCaseSuggestedAction`nomeada e a segunda nomeada. Ambas as <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>classes implementam .

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Ambas as classes são iguais, exceto que uma liga <xref:System.String.ToUpper%2A> e a outra chama. <xref:System.String.ToLower%2A> As etapas seguintes abrangem apenas a classe de ação maiúscula, mas você deve implementar ambas as classes. Use as etapas para implementar a ação maiúscula como padrão para a implementação da ação minúscula.

3. Adicione as seguintes diretivas usando para essas classes:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Declare um conjunto de campos privados.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Adicione um construtor que define os campos.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> o método para que ele exiba a visualização de ação.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> o método para que <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> ele retorne uma enumeração vazia.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implemente as propriedades da seguinte forma.

    ```csharp
    public bool HasActionSets
    {
        get { return false; }
    }
    public string DisplayText
    {
        get { return m_display; }
    }
    public ImageMoniker IconMoniker
    {
       get { return default(ImageMoniker); }
    }
    public string IconAutomationText
    {
        get
        {
            return null;
        }
    }
    public string InputGestureText
    {
        get
        {
            return null;
        }
    }
    public bool HasPreview
    {
        get { return true; }
    }
    ```

9. Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> o método substituindo o texto no vão por seu equivalente maiúsculo.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > O método **de invocação** da lâmpada não é esperado para mostrar ui. Se sua ação trouxer uma nova iu (por exemplo, uma visualização ou diálogo de seleção), não exiba a ui diretamente dentro do método **Invocar,** mas, em vez disso, programe-se para exibir sua iu depois de retornar de **Invoke**.

10. Para concluir a implementação, adicione os `Dispose()` métodos e. `TryGetTelemetryId()`

    ```csharp
    public void Dispose()
    {
    }

    public bool TryGetTelemetryId(out Guid telemetryId)
    {
        // This is a sample action and doesn't participate in LightBulb telemetry
        telemetryId = Guid.Empty;
        return false;
    }
    ```

11. Não se esqueça de fazer `LowerCaseSuggestedAction` a mesma coisa para{0}alterar o texto de <xref:System.String.ToUpper%2A> exibição para "Converter ' para minúscula" e a chamada para <xref:System.String.ToLower%2A>.

## <a name="build-and-test-the-code"></a>Construa e teste o código
 Para testar este código, construa a solução LightBulbTest e execute-a na instância Experimental.

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto. Você deve ver uma lâmpada à esquerda do texto.

     ![testar a lâmpada](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Aponte para a lâmpada. Você deveria ver uma flecha para baixo.

5. Quando você clica na lâmpada, duas ações sugeridas devem ser exibidas, juntamente com a visualização da ação selecionada.

     ![lâmpada de teste, expandido](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpandido")

6. Se você clicar na primeira ação, todo o texto na palavra atual deve ser convertido em maiúscula. Se você clicar na segunda ação, todo o texto deve ser convertido em minúscula.
