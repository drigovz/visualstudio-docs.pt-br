---
title: 'Walkthrough: exibindo dicas de ferramenta QuickInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b349f0293071dfa30677b7558ca93985d16d55e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838509"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Passo a passo: exibindo dicas de ferramenta de InformaçãoRápida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

QuickInfo é um recurso do IntelliSense que exibe assinaturas de método e descrições quando um usuário move o ponteiro sobre um nome de método. Você pode implementar recursos baseados em linguagem, como QuickInfo, definindo os identificadores para os quais você deseja fornecer descrições de QuickInfo e, em seguida, criando uma dica de ferramenta para exibir o conteúdo. Você pode definir QuickInfo no contexto de um serviço de idioma ou pode definir sua própria extensão de nome de arquivo e tipo de conteúdo e exibir o QuickInfo para apenas esse tipo, ou pode exibir QuickInfo para um tipo de conteúdo existente (como "texto"). Este tutorial mostra como exibir QuickInfo para o tipo de conteúdo "text".  
  
 O exemplo de QuickInfo neste passo a passos exibe as dicas de ferramenta quando um usuário move o ponteiro sobre um nome de método. Esse design exige que você implemente essas quatro interfaces:  
  
- interface de origem  
  
- interface do provedor de origem  
  
- interface do controlador  
  
- interface do provedor do controlador  
  
  Os provedores de origem e controlador são Managed Extensibility Framework (MEF) partes de componente e são responsáveis por exportar as classes de origem e controlador e importar serviços e agentes, como o <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , que cria o buffer de texto de dica de ferramenta e o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , que dispara a sessão QuickInfo.  
  
  Neste exemplo, a origem QuickInfo usa uma lista embutida em código de nomes e descrições de métodos, mas em implementações completas, o serviço de idioma e a documentação do idioma são responsáveis por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto do MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto do MEF  
  
1. Crie um projeto VSIX em C#. (Na caixa de diálogo **novo projeto** , selecione **Visual C#/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `QuickInfoTest` .  
  
2. Adicione um modelo de item de classificação do editor ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Exclua os arquivos de classe existentes.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementando a origem do QuickInfo  
 A origem QuickInfo é responsável por coletar o conjunto de identificadores e suas descrições e adicionar o conteúdo ao buffer de texto de dica de ferramenta quando um dos identificadores é encontrado. Neste exemplo, os identificadores e suas descrições são adicionados apenas no construtor de origem.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Para implementar a origem do QuickInfo  
  
1. Adicione um arquivo de classe e nomeie-o `TestQuickInfoSource` .  
  
2. Adicione uma referência a Microsoft. VisualStudio. Language. IntelliSense.  
  
3. Adicione as seguintes importações.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4. Declare uma classe que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> e nomeie-a `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5. Adicione campos para o provedor de origem QuickInfo, o buffer de texto e um conjunto de nomes de método e assinaturas de método. Neste exemplo, os nomes de método e as assinaturas são inicializados no `TestQuickInfoSource` Construtor.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6. Adicione um construtor que defina o provedor de origem QuickInfo e o buffer de texto e preencha o conjunto de nomes de método e as assinaturas e descrições de método.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A> . Neste exemplo, o método localiza a palavra atual ou a palavra anterior se o cursor estiver no final de uma linha ou um buffer de texto. Se a palavra for um dos nomes de método, a descrição desse nome de método será adicionada ao conteúdo QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8. Você também deve implementar um método Dispose (), desde que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implemente <xref:System.IDisposable> :  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementando um provedor de origem QuickInfo  
 O provedor da origem do QuickInfo serve principalmente para exportar a si mesmo como uma parte do componente do MEF e instanciar a origem do QuickInfo. Como é uma parte do componente do MEF, ele pode importar outras partes do componente do MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar um provedor de origem QuickInfo  
  
1. Declare um provedor de origem QuickInfo chamado `TestQuickInfoSourceProvider` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> e exporte-o com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "código-fonte QuickInfo", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes de = "default" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2. Importe dois serviços do editor <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> e <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , como propriedades de `TestQuickInfoSourceProvider` .  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para retornar um novo `TestQuickInfoSource` .  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementando um controlador QuickInfo  
 Os controladores QuickInfo determinam quando QuickInfo devem ser exibidos. Neste exemplo, QuickInfo é exibido quando o ponteiro está sobre uma palavra que corresponde a um dos nomes de método. O controlador QuickInfo implementa um manipulador de eventos de foco do mouse que dispara uma sessão QuickInfo.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Para implementar um controlador QuickInfo  
  
1. Declare uma classe que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> e nomeie-a `TestQuickInfoController` .  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2. Adicione campos particulares para a exibição de texto, os buffers de texto representados na exibição de texto, a sessão QuickInfo e o provedor do controlador QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3. Adicione um construtor que defina os campos e adicione o manipulador de eventos de foco do mouse.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4. Adicione o manipulador de eventos de foco do mouse que dispara a sessão QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5. Implemente o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> método para que ele remova o manipulador de eventos de foco do mouse quando o controlador for desanexado da exibição de texto.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6. Implemente o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> método e o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> método como métodos vazios para este exemplo.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementando o provedor do controlador QuickInfo  
 O provedor do controlador QuickInfo serve principalmente para exportar a si mesmo como uma parte de componente do MEF e instanciar o controlador QuickInfo. Como é uma parte do componente do MEF, ele pode importar outras partes do componente do MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar o provedor do controlador QuickInfo  
  
1. Declare uma classe denominada `TestQuickInfoControllerProvider` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> e exporte-a com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "controlador QuickInfo de dica de ferramenta" e um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2. Importe o <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como uma propriedade.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3. Implemente o <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> método instanciando o controlador QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
 Para testar esse código, crie a solução QuickInfoTest e execute-a na instância experimental.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para compilar e testar a solução QuickInfoTest  
  
1. Compile a solução.  
  
2. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3. Crie um arquivo de texto e digite algum texto que inclua as palavras "Adicionar" e "subtrair".  
  
4. Mova o ponteiro sobre uma das ocorrências de "Adicionar". A assinatura e a descrição do `add` método devem ser exibidas.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
