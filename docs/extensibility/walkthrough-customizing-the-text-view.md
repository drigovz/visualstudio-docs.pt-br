---
title: 'Passo a passo: Personalizando a visualização de texto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697463"
---
# <a name="walkthrough-customize-the-text-view"></a>Passo a passo: Personalize a visualização de texto
Você pode personalizar uma exibição de texto modificando qualquer uma das seguintes propriedades em seu mapa de formato de editor:

- Margem de indicadores

- Cuidador de inserção

- Superescrever caret

- Texto selecionado

- Texto selecionado inativo (ou seja, texto selecionado que perdeu o foco)

- Espaço em branco visível

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Crie um projeto MEF

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `ViewPropertyTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

## <a name="define-the-content-type"></a>Defina o tipo de conteúdo

1. Adicione um arquivo de `ViewPropertyModifier`classe e nomeie-o .

2. Adicione as seguintes diretivas `using`:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Declare uma `TestViewCreationListener` classe chamada <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>que herda de . Exporte esta classe com os seguintes atributos:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>para especificar o tipo de conteúdo ao qual este ouvinte se aplica.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>para especificar o papel deste ouvinte.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. Nesta classe, importe o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Alterar as propriedades de exibição

1. Configure <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> o método para que as propriedades de exibição sejam alteradas quando a exibição for aberta. Para fazer a mudança, <xref:System.Windows.ResourceDictionary> primeiro encontre o que corresponde ao aspecto da vista que você deseja encontrar. Em seguida, altere a propriedade apropriada no dicionário de recursos e defina as propriedades. Lote as chamadas <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> para o <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método chamando o método <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> antes de definir as propriedades e, em seguida, depois de definir as propriedades.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Construa e teste o código

1. Compile a solução.

     Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

2. Crie um arquivo de texto e digite algum texto.

    - O cuidado de inserção deve ser magenta e o caret de sobregravação deve ser turquesa.

    - A margem indicadora (à esquerda da exibição do texto) deve ser verde-claro.

3. Selecione o texto que você digitou. A cor do texto selecionado deve ser rosa claro.

4. Enquanto o texto estiver selecionado, clique em qualquer lugar fora da janela de texto. A cor do texto selecionado deve ser rosa escuro.

5. Ligue o espaço em branco visível. (No menu **Editar,** aponte para **Avançado** e clique **em Exibir espaço branco**). Digite algumas guias no texto. As setas vermelhas que representam as guias devem ser exibidas.

## <a name="see-also"></a>Confira também
- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
