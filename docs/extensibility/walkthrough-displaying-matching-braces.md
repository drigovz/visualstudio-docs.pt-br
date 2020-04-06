---
title: 'Passo a passo: Exibindo chaves correspondentes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697446"
---
# <a name="walkthrough-display-matching-braces"></a>Passo a passo: Exibir aparelhos correspondentes
Implemente recursos baseados em linguagem, como, a correspondência de chaves definindo os aparelhos que você deseja combinar, e adicionando uma etiqueta de marcador de texto às chaves correspondentes quando a careta estiver em uma das chaves. Você pode definir chaves no contexto de um idioma, definir a extensão e o tipo de conteúdo do seu próprio nome de arquivo e aplicar as tags apenas para esse tipo ou aplicar as tags a um tipo de conteúdo existente (como "texto"). O passo a passo a seguir mostra como aplicar tags de correspondência de chaves ao tipo de conteúdo "texto".

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Criar um projeto MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada)

#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF

1. Crie um projeto de classificador de editor. Diga a `BraceMatchingTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

## <a name="implement-a-brace-matching-tagger"></a>Implementar um tagger de correspondência de cinta
 Para obter um efeito de destaque da cinta que se assemelha ao que é <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>usado no Visual Studio, você pode implementar um tagger do tipo . O código a seguir mostra como definir o tagger para pares de chaves em qualquer nível de aninhamento. Neste exemplo, os pares de chaves {} de [] e são definidos no construtor tagger, mas em uma implementação completa da linguagem, os pares de chaves relevantes seriam definidos na especificação do idioma.

### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar um tagger de correspondência de cinta

1. Adicione um arquivo de classe e nomeie-o BraceMatching.

2. Importe os seguintes namespaces.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Defina `BraceMatchingTagger` uma classe <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> que <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>herda do tipo .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Adicione propriedades para a exibição de texto, o buffer de origem, o ponto de instantâneo atual e também um conjunto de pares de chaves.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. No construtor tagger, defina as propriedades e <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> assine <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>os eventos de alteração de exibição e . Neste exemplo, para fins ilustrativos, os pares correspondentes também são definidos na construtora.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Como parte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> da implementação, declare um evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Os manipuladores de eventos atualizam `CurrentChar` a posição atual da propriedade e aumentam o evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> o método para combinar aparelhos quando o personagem atual for uma cinta aberta ou quando o caractere anterior for uma cinta próxima, como no Visual Studio. Quando a correspondência é encontrada, este método instancia duas tags, uma para a cinta aberta e outra para a cinta próxima.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Os seguintes métodos privados encontram a cinta correspondente em qualquer nível de aninhamento. O primeiro método encontra o caractere próximo que corresponde ao caractere aberto:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. O seguinte método auxiliar encontra o caractere aberto que corresponde a um caractere próximo:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementar um provedor de tagger de correspondência de chaves
 Além de implementar um tagger, você também deve implementar e exportar um provedor de tagger. Neste caso, o tipo de conteúdo do provedor é "texto". Assim, a correspondência de chaves aparecerá em todos os tipos de arquivos de texto, mas uma implementação mais completa aplica a correspondência de chaves apenas a um tipo de conteúdo específico.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar um provedor de tagger compatível com a cinta

1. Declare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>um provedor de tagger que herda de , nomeá-lo BraceMatchingTaggerProvider, e exporte-o com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto" e a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> o método para instanciar um BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Construa e teste o código
 Para testar este código, construa a solução BraceMatchingTest e execute-o na instância experimental.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para construir e testar a solução BraceMatchingTest

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto que inclua aparelhos correspondentes.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Quando você posicionar a careta antes de uma cinta aberta, tanto a cinta quanto a cinta de correspondência devem ser destacadas. Quando você posicionar o cursor logo após a cinta de fechamento, tanto a cinta quanto a cinta aberta correspondente devem ser destacadas.

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
