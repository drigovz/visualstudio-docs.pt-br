---
title: 'Passo a passo: Vinculando um tipo de conteúdo a uma extensão de nome de arquivo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697080"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo
Você pode definir seu próprio tipo de conteúdo e vincular uma extensão de nome de arquivo a ele usando as extensões mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada gerenciada) do editor. Em alguns casos, a extensão do nome do arquivo já é definida por um serviço de idioma. Mas, para usá-lo com MEF, você ainda deve vinculá-lo a um tipo de conteúdo.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Crie um projeto MEF

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `ContentTypeTest`solução.

2. No arquivo **source.extension.vsixmanifest,** vá para a guia **'Ativos'** e defina o campo **Tipo** para **Microsoft.VisualStudio.MefComponent**, o campo **Origem** para **A na solução atual**e o campo **Projeto** para o nome do projeto.

## <a name="define-the-content-type"></a>Defina o tipo de conteúdo

1. Adicione um arquivo de `FileAndContentTypes`classe e nomeie-o .

2. Adicione referências aos assemblies a seguir:

    1. System.ComponentModel.Composition

    2. Microsoft.visualStudio.text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Adicione as `using` seguintes diretivas.

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

5. Nesta classe, exporte um <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> chamado "escondido" e declare sua definição base como "texto".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Vincule uma extensão de nome de arquivo a um tipo de conteúdo

- Para mapear esse tipo de conteúdo para <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> uma extensão de nome de arquivo, exporte um que tenha a extensão *.hid e* o tipo de conteúdo "escondido".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Adicione o tipo de conteúdo a uma exportação de editor

1. Crie uma extensão de editor. Por exemplo, você pode usar a extensão de glifo de margem descrita no [Passo a Passo: Crie um glifo de margem](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Adicione a classe definida neste procedimento.

3. Ao exportar a classe de <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> extensão, adicione um tipo "escondido" a ela.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Confira também
- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
