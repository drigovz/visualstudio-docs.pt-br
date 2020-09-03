---
title: 'Walkthrough: estrutura de tópicos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c1dd3d28b9978b52c95b5ff905d57720ed10f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201965"
---
# <a name="walkthrough-outlining"></a>Passo a passo: estrutura de tópicos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode implementar recursos baseados em linguagem, como estrutura de tópicos, definindo os tipos de regiões de texto que deseja expandir ou recolher. Você pode definir regiões no contexto de um serviço de idioma ou pode definir sua própria extensão de nome de arquivo e tipo de conteúdo e aplicar a definição de região a apenas esse tipo, ou você pode aplicar as definições de região a um tipo de conteúdo existente (como "texto"). Este tutorial mostra como definir e exibir regiões de estrutura de tópicos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto do MEF  
  
1. Crie um projeto VSIX. Nomeie a solução `OutlineRegionTest` .  
  
2. Adicione um modelo de item de classificação do editor ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Exclua os arquivos de classe existentes.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementando um marca-estruturador de tópicos  
 As regiões de estrutura de tópicos são marcadas por um tipo de marca ( <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> ). Essa marca fornece o comportamento de estrutura de tópicos padrão. A região contornada pode ser expandida ou recolhida. A região contornada será marcada por um sinal de adição se for recolhida ou um sinal de subtração se for expandido e a região expandida for demarcadasda por uma linha vertical.  
  
 As etapas a seguir mostram como definir um marcador que cria regiões de estrutura de tópicos para todas as regiões delimitadas por "[" e "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Para implementar um marca-estruturador de tópicos  
  
1. Adicione um arquivo de classe e nomeie-o `OutliningTagger` .  
  
2. Importe os namespaces a seguir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#1)]
     [!code-vb[VSSDKOutlineRegionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#1)]  
  
3. Crie uma classe chamada `OutliningTagger` e implemente-a <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> :  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#2)]
     [!code-vb[VSSDKOutlineRegionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#2)]  
  
4. Adicione alguns campos para acompanhar o buffer de texto e o instantâneo e para acumular os conjuntos de linhas que devem ser marcados como regiões de estrutura de tópicos. Esse código inclui uma lista de objetos Region (a serem definidos posteriormente) que representam as regiões de estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#3)]
     [!code-vb[VSSDKOutlineRegionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#3)]  
  
5. Adicione um construtor de marcação que inicializa os campos, analisa o buffer e adiciona um manipulador de eventos ao <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#4)]
     [!code-vb[VSSDKOutlineRegionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#4)]  
  
6. Implemente o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método, que instancia as extensões de marca. Este exemplo supõe que as extensões em <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passado para o método são contíguas, embora isso não possa ser sempre o caso. Esse método instancia um novo Span de marca para cada uma das regiões de estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#5)]
     [!code-vb[VSSDKOutlineRegionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#5)]  
  
7. Declare um `TagsChanged` manipulador de eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#6)]
     [!code-vb[VSSDKOutlineRegionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#6)]  
  
8. Adicione um `BufferChanged` manipulador de eventos que responda a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos analisando o buffer de texto.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#7)]
     [!code-vb[VSSDKOutlineRegionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#7)]  
  
9. Adicione um método que analisa o buffer. O exemplo fornecido aqui é apenas para ilustração. Ele analisa de forma síncrona o buffer em regiões aninhadas da estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#8)]
     [!code-vb[VSSDKOutlineRegionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#8)]  
  
10. O método auxiliar a seguir obtém um inteiro que representa o nível da estrutura de tópicos, de modo que 1 é o par de chaves mais à esquerda.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#9)]
     [!code-vb[VSSDKOutlineRegionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#9)]  
  
11. O método auxiliar a seguir converte uma região (definida mais adiante neste tópico) em um SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#10)]
     [!code-vb[VSSDKOutlineRegionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#10)]  
  
12. O código a seguir é apenas para ilustração. Ele define uma classe PartialRegion que contém o número de linha e o deslocamento do início de uma região de estrutura de tópicos e também uma referência à região pai (se houver). Isso permite que o analisador configure regiões de estrutura de tópicos aninhadas. Uma classe de região derivada contém uma referência ao número de linha do final de uma região de estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#11)]
     [!code-vb[VSSDKOutlineRegionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#11)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementando um provedor de marcador  
 Você deve exportar um provedor de marcação para o seu marcador. O provedor de marcação cria um `OutliningTagger` para um buffer do tipo de conteúdo "text" ou, caso contrário, retorna um `OutliningTagger` se o buffer já tiver um.  
  
#### <a name="to-implement-a-tagger-provider"></a>Para implementar um provedor de marcador  
  
1. Crie uma classe chamada `OutliningTaggerProvider` que implementa e <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> exporte-a com os atributos ContentType e TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#12)]
     [!code-vb[VSSDKOutlineRegionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#12)]  
  
2. Implemente o <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método adicionando um `OutliningTagger` às propriedades do buffer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkoutlineregiontest/cs/outliningtagger.cs#13)]
     [!code-vb[VSSDKOutlineRegionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkoutlineregiontest/vb/outliningtagger.vb#13)]  
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
 Para testar esse código, crie a solução OutlineRegionTest e execute-a na instância experimental.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar e testar a solução OutlineRegionTest  
  
1. Compile a solução.  
  
2. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3. Crie um arquivo de texto. Digite um texto que inclua a chave de abertura e a chave de fechamento.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4. Deve haver uma região de estrutura de tópicos que inclua ambas as chaves. Você deve ser capaz de clicar no sinal de subtração à esquerda da chave de abertura para recolher a região de estrutura de tópicos. Quando a região é recolhida, o símbolo de reticências (...) deve aparecer à esquerda da região recolhida e um pop-up contendo o **texto de foco** do texto deve aparecer quando você move o ponteiro sobre as reticências.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
