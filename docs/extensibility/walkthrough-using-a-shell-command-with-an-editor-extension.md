---
title: 'Passo a passo: Usando um comando Shell com uma extensão do editor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697165"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Passo a passo: Use um comando shell com uma extensão de editor
A partir de um VSPackage, você pode adicionar recursos como comandos de menu ao editor. Este passo a passo mostra como adicionar um adorno a uma exibição de texto no editor invocando um comando de menu.

 Este passo a passo demonstra o uso de um VSPackage juntamente com uma parte componente MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada). Você deve usar um VSPackage para registrar o comando menu com o shell do Visual Studio. E você pode usar o comando para acessar a parte do componente MEF.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Crie uma extensão com um comando de menu
 Crie um VSPackage que coloca um comando de menu chamado **Adicionar Adorno** no menu **Ferramentas.**

1. Crie um projeto C# `MenuCommandTest`VSIX chamado e adicione o nome de modelo de item de comando personalizado **AddAdornment**. Para obter mais informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Uma solução chamada MenuCommandTest é aberta. O arquivo MenuCommandTestPackage tem o código que cria o comando menu e o coloca no menu **Ferramentas.** Neste ponto, o comando apenas faz com que uma caixa de mensagem apareça. Etapas posteriores mostrarão como alterar isso para exibir o adorno de comentários.

3. Abra o arquivo *source.extension.vsixmanifest* no Editor de Manifesto vsix. A `Assets` guia deve ter uma linha para um Microsoft.VisualStudio.VsPackage chamado MenuCommandTest.

4. Salvar e fechar o arquivo *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Adicione uma extensão MEF à extensão de comando

1. No **Solution Explorer,** clique com o botão direito do mouse no nó da solução, clique em **Adicionar**e clique em **Novo Projeto**. Na caixa de diálogo **Adicionar novo projeto,** clique **em Extensibilidade** em **Visual C#**, em seguida, **Projeto VSIX**. Dê ao projeto o nome de `CommentAdornmentTest`.

2. Como este projeto interagirá com o conjunto VSPackage, com o nome mais forte, você deve assinar a montagem. Você pode reutilizar o arquivo-chave já criado para o conjunto VSPackage.

    1. Abra as propriedades do projeto e selecione a guia **Assinatura.**

    2. Selecione **Assinar o conjunto**.

    3. Em **Escolha um arquivo de chave de nome forte,** selecione o arquivo *Key.snk* gerado para o conjunto MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Consulte a extensão MEF no projeto VSPackage
 Como você está adicionando um componente MEF ao VSPackage, você deve especificar ambos os tipos de ativos no manifesto.

> [!NOTE]
> Para obter mais informações sobre o MEF, consulte [Quadro de Extensibilidade Gerenciada (MEF).](/dotnet/framework/mef/index)

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Para consultar o componente MEF no projeto VSPackage

1. No projeto MenuCommandTest, abra o arquivo *source.extension.vsixmanifest* no Editor de Manifesto vsix.

2. Na guia **Ativos,** clique em **Novo**.

3. Na lista **Tipo,** escolha **Microsoft.VisualStudio.MefComponent**.

4. Na lista **Origem,** escolha **Um projeto na solução atual**.

5. Na lista **Projeto,** escolha **CommentAdornTest**.

6. Salvar e fechar o arquivo *source.extension.vsixmanifest.*

7. Certifique-se de que o projeto MenuCommandTest tenha uma referência ao projeto CommentAdornmentTest.

8. No projeto CommentAdornmentTest, defina o projeto para produzir uma montagem. No **Explorador de soluções,** selecione o projeto e procure na janela **Propriedades** para a propriedade **Copiar construção de saída para outputDirectory** e defina-a **como true**.

## <a name="define-a-comment-adornment"></a>Defina um adorno de comentários
 O adorno de comentários <xref:Microsoft.VisualStudio.Text.ITrackingSpan> em si consiste em um que rastreia o texto selecionado, e algumas cordas que representam o autor e a descrição do texto.

#### <a name="to-define-a-comment-adornment"></a>Para definir um adorno de comentários

1. No projeto CommentAdornmentTest, adicione um novo `CommentAdornment`arquivo de classe e nomeie-o .

2. Adicione as seguintes referências:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.visualStudio.text.Logic

    4. Microsoft.visualStudio.text.ui

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Composition

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Adicione a `using` seguinte diretiva.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. O arquivo deve conter `CommentAdornment`uma classe chamada .

    ```csharp
    internal class CommentAdornment
    ```

5. Adicione três campos `CommentAdornment` à <xref:Microsoft.VisualStudio.Text.ITrackingSpan>classe para o , o autor, e a descrição.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Adicione um construtor que inicialize os campos.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Crie um elemento visual para o adorno
 Defina um elemento visual para o seu adorno. Para este passo a passo, defina um controle que herda da classe WPF (Windows Presentation Foundation, fundação de apresentação <xref:System.Windows.Controls.Canvas>do Windows).

1. Crie uma classe no projeto CommentAdornmentTest `CommentBlock`e nomeie-a .

2. Adicione as `using` seguintes diretivas.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Faça `CommentBlock` a classe <xref:System.Windows.Controls.Canvas>herdar de .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Adicione alguns campos privados para definir os aspectos visuais do adorno.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Adicione um construtor que define o adorno de comentários e adiciona o texto relevante.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Implemente <xref:System.Windows.Controls.Panel.OnRender%2A> também um manipulador de eventos que desente o adorno.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Adicionar um IWpfTextViewCreationListener
 A <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> parte é um componente MEF que você pode usar para ouvir eventos de criação.

1. Adicione um arquivo de classe ao projeto `Connector`CommentAdornmentTest e nomeie-o .

2. Adicione as `using` seguintes diretivas.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Declare uma classe <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>que implemente , <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> e exporte-a com um de "texto" e um <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. O atributo tipo de conteúdo especifica o tipo de conteúdo ao qual o componente se aplica. O tipo de texto é o tipo base para todos os tipos de arquivos não binários. Portanto, quase todas as visualizações de texto criadas serão desse tipo. O atributo função de exibição de texto especifica o tipo de exibição de texto a que o componente se aplica. As funções de exibição de texto do documento geralmente mostram o texto que é composto por linhas e é armazenado em um arquivo.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementar <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> o método para que `Create()` ele chame `CommentAdornmentManager`o evento estático do .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Adicione um método que você pode usar para executar o comando.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Defina uma camada de adorno
 Para adicionar um novo adorno, você deve definir uma camada de adorno.

### <a name="to-define-an-adornment-layer"></a>Para definir uma camada de adorno

1. Na `Connector` classe, declare um campo <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>público de tipo <xref:Microsoft.VisualStudio.Utilities.NameAttribute> e exporte-o com um que <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> especifica um nome único para a camada de adorno e que define a relação de ordem Z desta camada de adorno para as outras camadas de exibição de texto (texto, cuidado e seleção).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Fornecer adornos de comentários
 Quando você define um adorno, também implemente um provedor de adornos de comentários e um gerente de adorno de comentários. O provedor de adornos de comentários mantém uma <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> lista de adornos de comentários, ouve eventos no buffer de texto subjacente e exclui adornos de comentários quando o texto subjacente é excluído.

1. Adicione um novo arquivo de classe ao projeto `CommentAdornmentProvider`CommentAdornmentTest e nomeie-o .

2. Adicione as `using` seguintes diretivas.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Adicione uma classe chamada `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Adicione campos privados para o buffer de texto e a lista de adornos de comentários relacionados ao buffer.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Adicione um construtor `CommentAdornmentProvider`para . Este construtor deve ter acesso privado porque o provedor `Create()` é instanciado pelo método. O construtor adiciona `OnBufferChanged` o manipulador <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> de eventos ao evento.

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Adicione o método `Create()`.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Adicione o método `Detach()`.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Adicione `OnBufferChanged` o manipulador de eventos.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Adicione uma declaração para um `CommentsChanged` evento.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Crie `Add()` um método para adicionar o adorno.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Adicione `RemoveComments()` um método.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Adicione `GetComments()` um método que retorna todos os comentários em um determinado período de instantâneo.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Adicione uma `CommentsChangedEventArgs`classe chamada , da seguinte forma.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Gerencie adornos de comentários
 O gerente de adorno de comentários cria o adorno e adiciona-o à camada de adorno. Ele ouve os <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> eventos e eventos para que ele possa mover ou excluir o adorno. Ele também ouve `CommentsChanged` o evento que é disparado pelo provedor de adornos de comentários quando os comentários são adicionados ou removidos.

1. Adicione um arquivo de classe ao projeto `CommentAdornmentManager`CommentAdornmentTest e nomeie-o .

2. Adicione as `using` seguintes diretivas.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Adicione uma classe chamada `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Adicione alguns campos privados.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Adicione um construtor que inscreva o <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> gerente para os `CommentsChanged` eventos e também para o evento. O construtor é privado porque o gerente é `Create()` instanciado pelo método estático.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Adicione `Create()` o método que obtém um provedor ou cria um, se necessário.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Adicione `CommentsChanged` o manipulador.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Adicione <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> o manipulador.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Adicione <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> o manipulador.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Adicione o método privado que desenha o comentário.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Use o comando menu para adicionar o adorno de comentários
 Você pode usar o comando menu para criar `MenuItemCallback` um adorno de comentários implementando o método do VSPackage.

1. Adicione as seguintes referências ao projeto MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Abra o *arquivo AddAdornment.cs* `using` e adicione as seguintes diretivas.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Exclua `Execute()` o método e adicione o seguinte manipulador de comando.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Adicione código para obter a exibição ativa. Você deve `SVsTextManager` obter a concha do Visual `IVsTextView`Studio para obter o ativo .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Se esta exibição de texto for uma instância de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> uma exibição <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> de texto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>do editor, você pode lançá-la para a interface e, em seguida, obter o e sua associated . Use <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> o para `Connector.Execute()` chamar o método, que recebe o provedor de adorno de comentários e adiciona o adorno. O manipulador de comando deve agora se parecer com este código:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Defina o método AddAdornmentHandler como o manipulador do comando AddAdornment no construtor AddAdornment.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Construa e teste o código

1. Compile a solução e inicie a depuração. A instância experimental deve aparecer.

2. Crie um arquivo de texto. Digite algum texto e selecione-o.

3. No menu **Ferramentas,** clique **em Invocar Adicionar adorno**. Um balão deve ser exibido no lado direito da janela de texto e deve conter um texto que se assemelhe ao texto a seguir.

     SeuNome de Usuário

     Fourscore...

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
