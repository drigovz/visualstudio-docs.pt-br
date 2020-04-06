---
title: 'Passo a passo: Delineando | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697222"
---
# <a name="walkthrough-outlining"></a>Passo a passo: estrutura de tópicos
Configure recursos baseados em idioma, como delinear definindo os tipos de regiões de texto que você deseja expandir ou entrar em colapso. Você pode definir regiões no contexto de um serviço de idioma, ou definir a extensão e o tipo de conteúdo do seu próprio nome de arquivo e aplicar a definição de região apenas a esse tipo, ou aplicar as definições de região a um tipo de conteúdo existente (como "texto"). Este passo a passo mostra como definir e exibir regiões delineamento.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Criar um projeto MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada)

### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF

1. Crie um projeto VSIX. Diga a `OutlineRegionTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

## <a name="implement-an-outlining-tagger"></a>Implementar um tagger delineamento
 As regiões delineamento são marcadas por uma espécie de tag ().<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> Esta tag fornece o comportamento padrão de delineamento. A região delineada pode ser expandida ou colapsada. A região delineada é**+** marcada por um sinal Plus**-**( ) se ele está colapsado ou um sinal de Menos ( ) se for expandido, e a região expandida é demarcada por uma linha vertical.

 As etapas a seguir mostram como definir um tagger que cria regiões delineamento para todas as regiões delimitadas pelos suportes (**[****).**

### <a name="to-implement-an-outlining-tagger"></a>Para implementar um tagger delineamento

1. Adicione um arquivo de `OutliningTagger`classe e nomeie-o .

2. Importe os seguintes namespaces.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Crie uma `OutliningTagger`classe nomeada e <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>implemente::

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Adicione alguns campos para rastrear o buffer de texto e o snapshot e para acumular os conjuntos de linhas que devem ser marcados como regiões delineamento. Este código inclui uma lista de objetos da Região (a serem definidos posteriormente) que representam as regiões delineamento.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Adicione um construtor tagger que inicialize os campos, analise o buffer <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> e adicione um manipulador de eventos ao evento.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> o método, que instancia os intervalos de marcação. Este exemplo pressupõe que <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> os vãos passados para o método são contíguos, embora nem sempre seja o caso. Este método instancia um novo período de tag para cada uma das regiões delineamento.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Declare `TagsChanged` um manipulador de eventos.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Adicione `BufferChanged` um manipulador de <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos que responda a eventos analisando o buffer de texto.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Adicione um método que analisa o buffer. O exemplo dado aqui é apenas para ilustração. Ele analisa sincronizadamente o buffer em regiões aninhadas delineando.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. O seguinte método auxiliar recebe um inteiro que representa o nível do delineamento, de modo que 1 é o par de cinta mais à esquerda.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. O seguinte método auxiliar traduz uma região (definida posteriormente neste artigo) em um SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. O código a seguir é apenas para ilustração. Ele define uma classe PartialRegion que contém o número da linha e a compensação do início de uma região delineamento e uma referência à região-mãe (se houver). Este código permite que o analisador configure regiões delineamento aninhados. Uma classe Região derivada contém uma referência ao número de linha do final de uma região delineamento.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Implementar um provedor de tagger
 Exporte um provedor de tagger para o seu tagger. O provedor de `OutliningTagger` tagger cria um buffer do tipo de `OutliningTagger` conteúdo "texto", ou então retorna um se o buffer já tiver um.

### <a name="to-implement-a-tagger-provider"></a>Para implementar um provedor de tagger

1. Crie uma `OutliningTaggerProvider` classe nomeada <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>que implemente e exporte-a com os atributos ContentType e TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> o método `OutliningTagger` adicionando um às propriedades do buffer.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Construa e teste o código
 Para testar esse código, construa a solução OutlineRegionTest e execute-o na instância experimental.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para construir e testar a solução OutlineRegionTest

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto. Digite algum texto que inclua os suportes de abertura e os suportes de fechamento.

    ```
    [
       Hello
    ]
    ```

4. Deve haver uma região delineamento que inclua ambos os suportes. Você deve ser capaz de clicar no Sinal de Menos à esquerda do suporte aberto para colapsar a região de delineamento. Quando a região é colapsada, o símbolo ellipsis (*...*) deve aparecer à esquerda da região colapsada, e um popup contendo o **texto do hover** de texto deve aparecer quando você mover o ponteiro sobre a elipse.

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
