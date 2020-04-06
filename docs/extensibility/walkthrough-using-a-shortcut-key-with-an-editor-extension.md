---
title: 'Passo a passo: Usando uma tecla de atalho com uma extensão do editor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697147"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Passo a passo: Use uma tecla de atalho com uma extensão de editor
Você pode responder a teclas de atalho na extensão do editor. O passo a passo a seguir mostra como adicionar um adorno de exibição a uma exibição de texto usando uma tecla de atalho. Este passo a passo é baseado no modelo de editor de adornos de viewport, e permite adicionar o adorno usando o + caractere.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Criar um projeto MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada)

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `KeyBindingTest`solução.

2. Adicione um modelo de item de adornamento `KeyBindingTest`de texto do editor ao projeto e nomeie-o . Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Adicione as seguintes referências `false`e defina **CopyLocal** para:

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   No arquivo de classe KeyBindingAtTest, altere o nome da classe para PurpleCornerBox. Use a lâmpada que aparece na margem esquerda para fazer as outras mudanças apropriadas. Dentro do construtor, altere o nome da camada de adorno de **KeyBindingTest** para **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

No arquivo de classe KeyBindingTestTextViewCreationListener.cs, altere o nome do AdornmentLayer de **KeyBindingTest** para **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Lidar com o comando TYPECHAR
Antes do Visual Studio 2017 versão 15.6 a única maneira de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lidar com comandos em uma extensão de editor era implementando um filtro de comando baseado. Visual Studio 2017 versão 15.6 introduziu uma abordagem simplificada moderna baseada em manipuladores de comando de editor. As duas próximas seções demonstram como lidar com um comando usando o legado e a abordagem moderna.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Defina o filtro de comando (antes do Visual Studio 2017 versão 15.6)

 O filtro de comando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>é uma implementação de , que lida com o comando instanciando o adorno.

1. Adicione um arquivo de `KeyBindingCommandFilter`classe e nomeie-o .

2. Adicione as seguintes diretivas usando.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. A classe chamada KeyBindingCommandFilter <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>deve herdar de .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Adicione campos privados para a exibição de texto, o próximo comando na cadeia de comando e uma bandeira para representar se o filtro de comando já foi adicionado.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Adicione um construtor que define a exibição de texto.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implemente `QueryStatus()` o método da seguinte forma.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implemente `Exec()` o método de modo que ele adicione uma**+** caixa roxa à exibição se um caractere de sinal positivo () for digitado.

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Adicione o filtro de comando (antes do Visual Studio 2017 versão 15.6)
 O provedor de adorno deve adicionar um filtro de comando à exibição de texto. Neste exemplo, o provedor <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> implementa para ouvir eventos de criação de visualização de texto. Este fornecedor de adornos também exporta a camada de adorno, que define a ordem Z do adorno.

1. No arquivo KeyBindingBindingTestViewCreationListener, adicione as seguintes diretivas usando:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2. Para obter o adaptador de visualização de texto, você deve importar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Alterar <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> o método para que `KeyBindingCommandFilter`ele adicione o .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. O `AddCommandFilter` manipulador recebe o adaptador de exibição de texto e adiciona o filtro de comando.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementar um manipulador de comando (a partir da versão 15.6 do Visual Studio 2017)

Primeiro, atualize as referências do Nuget do projeto para fazer referência à API do editor mais recente:

1. Clique com o botão direito do mouse no projeto e **selecione Gerenciar pacotes nuget**.

2. No **Nuget Package Manager,** selecione a guia **Atualizações,** selecione a caixa de seleção **Selecionar todos os pacotes** e, em seguida, selecione **Atualizar**.

O manipulador de comando <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>é uma implementação de , que lida com o comando instanciando o adorno.

1. Adicione um arquivo de `KeyBindingCommandHandler`classe e nomeie-o .

2. Adicione as seguintes diretivas usando.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. A classe denominada KeyBindingCommandHandler deve herdar `ICommandHandler<TypeCharCommandArgs>`e exportá-la como: <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Adicionar um nome de exibição do manipulador de comando:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implemente `GetCommandState()` o método da seguinte forma. Como este manipulador de comando lida com o comando TYPECHAR do editor principal, ele pode delegar a habilitação do comando para o editor principal.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implemente `ExecuteCommand()` o método de modo que ele adicione uma**+** caixa roxa à exibição se um caractere de sinal positivo () for digitado.

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```

   7. Copiar a definição da camada de adorno *de KeyBindingTestTextViewCreationListener.cs* arquivo para o *KeyBindingCommandHandler.cs* e, em seguida, excluir *KeyBindingTestTextViewCreationListener.cs* arquivo:

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>Faça o adorno aparecer em cada linha

O adorno original apareceu em cada caractere 'a' em um arquivo de texto. Agora que mudamos o código para adicionar o **+** adorno em resposta ao personagem, **+** ele adiciona o adorno apenas na linha onde o personagem é digitado. Podemos alterar o código de adorno para que o adorno mais uma vez apareça em cada 'a'.

No *arquivo KeyBindingTest.cs,* `CreateVisuals()` altere o método para iterar através de todas as linhas na vista para decorar o caractere 'a'.

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>Construa e teste o código

1. Construa a solução KeyBindingTest e execute-a na instância experimental.

2. Crie ou abra um arquivo de texto. Digite algumas palavras que contenham o **+** caractere 'a' e digite em qualquer lugar na exibição de texto.

     Um quadrado roxo deve aparecer em cada caractere 'a' no arquivo.
