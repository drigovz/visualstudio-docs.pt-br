---
title: 'Walkthrough: usando uma tecla de atalho com uma extensão de editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201943"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Passo a passo: usando uma tecla de atalho com uma extensão do editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode responder às teclas de atalho na extensão do editor. A instrução a seguir mostra como adicionar uma exibição Adornment a uma exibição de texto usando uma tecla de atalho. Este passo a passos é baseado no modelo do editor de Adornment do visor e permite que você adicione o Adornment usando o caractere +.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto Managed Extensibility Framework (MEF)  
  
1. Crie um projeto VSIX em C#. (Na caixa de diálogo **novo projeto** , selecione **Visual C#/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `KeyBindingTest` .  
  
2. Adicione um modelo de item Adornment de texto do editor ao projeto e nomeie-o `KeyBindingTest` . Para obter mais informações, consulte [criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Adicione as seguintes referências e defina **CopyLocal** como `false` :  
  
    Microsoft. VisualStudio. editor  
  
    Microsoft. VisualStudio. OLE. Interop  
  
    Microsoft. VisualStudio. Shell. 14.0  
  
    Microsoft. VisualStudio. Textmanager. Interop  
  
   No arquivo da classe KeyBindingTest, altere o nome da classe para PurpleCornerBox. Use a lâmpada que aparece na margem esquerda para fazer as outras alterações apropriadas. Dentro do Construtor, altere o nome da camada Adornment de **KeyBindingTest** para **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definindo o filtro de comando  
 O filtro de comando é uma implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , que manipula o comando ao instanciar o Adornment.  
  
1. Adicione um arquivo de classe e nomeie-o `KeyBindingCommandFilter` .  
  
2. Adicionar as seguintes instruções de uso.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. A classe denominada KeyBindingCommandFilter deve herdar de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. Adicione campos particulares para a exibição de texto, o próximo comando na cadeia de comandos e um sinalizador para representar se o filtro de comando já foi adicionado.  
  
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
  
6. Implemente o `QueryStatus()` método da seguinte maneira.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Implemente o `Exec()` método para que ele adicione uma caixa roxa à exibição se um caractere + for digitado.  
  
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
  
## <a name="adding-the-command-filter"></a>Adicionando o filtro de comando  
 O provedor Adornment deve adicionar um filtro de comando à exibição de texto. Neste exemplo, o provedor implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para escutar eventos de criação de exibição de texto. Esse provedor Adornment também exporta a camada Adornment, que define a ordem Z do Adornment.  
  
1. No arquivo KeyBindingTestTextViewCreationListener, adicione as seguintes instruções using:  
  
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
  
2. Na definição da camada Adornment, altere o nome do AdornmentLayer de **KeyBindingTest** para **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Para obter o adaptador de exibição de texto, você deve importar o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Altere o <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que ele adicione o `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. O `AddCommandFilter` manipulador obtém o adaptador de exibição de texto e adiciona o filtro de comando.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Fazendo o Adornment aparecer em todas as linhas  
 O Adornment original apareceu em cada caractere ' a ' em um arquivo de texto. Agora que alteramos o código para adicionar o Adornment em resposta ao caractere ' + ', ele adiciona o Adornment somente na linha em que o ' + ' é digitado. Podemos alterar o código Adornment para que o Adornment mais uma vez apareça em cada ' a '.  
  
 No arquivo KeyBindingTest.cs, altere o método createvisuals () para iterar por todas as linhas na exibição para decorar o caractere ' a '.  
  
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
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
  
1. Crie a solução KeyBindingTest e execute-a na instância experimental.  
  
2. Criar ou abrir um arquivo de texto. Digite algumas palavras que contenham o caractere ' a ' e, em seguida, digite + em qualquer lugar na exibição de texto.  
  
     Um quadrado roxo deve aparecer em cada caractere ' a ' no arquivo.
