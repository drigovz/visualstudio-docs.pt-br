---
title: 'Walkthrough: vinculando um tipo de conteúdo a uma extensão de nome de arquivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202002"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Passo a passo: vinculando um tipo de conteúdo a uma extensão de nome de arquivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode definir seu próprio tipo de conteúdo e vincular uma extensão de nome de arquivo a ele usando extensões de Managed Extensibility Framework do editor (MEF). Em alguns casos, a extensão de nome de arquivo já foi definida por um serviço de linguagem; no entanto, para usá-lo com o MEF, você ainda deve vinculá-lo a um tipo de conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto do MEF  
  
1. Crie um projeto VSIX em C#. (Na caixa de diálogo **novo projeto** , selecione **Visual C#/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `ContentTypeTest` .  
  
2. No arquivo **Source. Extension. vsixmanifest** , vá para a guia **ativos** e defina o campo **tipo** como **Microsoft. VisualStudio. MefComponent**, o campo de **origem** para **um projeto na solução atual**e o campo **projeto** como o nome do projeto.  
  
## <a name="defining-the-content-type"></a>Definindo o tipo de conteúdo  
  
1. Adicione um arquivo de classe e nomeie-o `FileAndContentTypes` .  
  
2. Adicione referências aos assemblies a seguir:  
  
    1. System. ComponentModel. composição  
  
    2. Microsoft. VisualStudio. Text. Logic  
  
    3. Microsoft. VisualStudio. CoreUtility  
  
3. Adicione as seguintes `using` diretivas.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4. Declare uma classe estática que contenha as definições.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5. Nessa classe, exporte um <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> chamado "HID" e declare sua definição de base como "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Vinculando uma extensão de nome de arquivo a um tipo de conteúdo  
  
- Para mapear esse tipo de conteúdo para uma extensão de nome de arquivo, exporte um <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tenha a extensão ". HID" e o tipo de conteúdo "HID".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Adicionando o tipo de conteúdo a uma exportação do editor  
  
1. Crie uma extensão de editor. Por exemplo, você pode usar a extensão de glifo de margem descrita em [Walkthrough: Criando um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Adicione a classe que você definiu neste procedimento.  
  
3. Ao exportar a classe de extensão, adicione um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> do tipo "HID" a ela.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Consulte Também  
 [Serviço de linguagem e pontos de extensão do editor](../extensibility/language-service-and-editor-extension-points.md)
