---
title: 'Walkthrough: exibindo a ajuda da assinatura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 280b5b517089ad9e5b38cb00dc9b14c68253d1e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202043"
---
# <a name="walkthrough-displaying-signature-help"></a>Passo a passo: exibindo a ajuda da assinatura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A ajuda da assinatura (também conhecida como *informações do parâmetro*) exibe a assinatura de um método em uma dica de ferramenta quando um usuário digita o caractere de início da lista de parâmetros (normalmente um parêntese de abertura). Como um separador de parâmetro e parâmetro (normalmente uma vírgula) são digitados, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito. Você pode definir a ajuda da assinatura no contexto de um serviço de idioma ou pode definir sua própria extensão de nome de arquivo e tipo de conteúdo e exibir a ajuda da assinatura apenas para esse tipo, ou pode exibir a ajuda da assinatura para um tipo de conteúdo existente (por exemplo, "texto"). Este tutorial mostra como exibir a ajuda da assinatura para o tipo de conteúdo "texto".  
  
 A ajuda da assinatura é normalmente disparada digitando um caractere específico, por exemplo, "(" (parêntese de abertura) e descartado digitando outro caractere, por exemplo, ")" (parêntese de fechamento). Os recursos do IntelliSense que são disparados pela digitação de um caractere podem ser implementados usando um manipulador de comando para os pressionamentos de tecla (a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e um provedor de manipulador que implementa a <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Para criar a fonte de ajuda da assinatura, que é a lista de assinaturas que participam da ajuda da assinatura, implemente a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interface e um provedor de origem que implementa a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interface. Os provedores são partes de componente Managed Extensibility Framework (MEF) e são responsáveis por exportar as classes de origem e controlador e importar serviços e agentes, por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que permite que você navegue no buffer de texto e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> , que dispara a sessão de ajuda de assinatura.  
  
 Este tutorial mostra como implementar a ajuda de assinatura para um conjunto de identificadores embutido em código. Em implementações completas, a linguagem é responsável por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto do MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto do MEF  
  
1. Crie um projeto VSIX em C#. (Na caixa de diálogo **novo projeto** , selecione **Visual C#/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `SignatureHelpTest` .  
  
2. Adicione um modelo de item de classificação do editor ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Exclua os arquivos de classe existentes.  
  
4. Adicione as seguintes referências ao projeto e verifique se **CopyLocal** está definido como `false` :  
  
     Microsoft. VisualStudio. editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. Textmanager. Interop  
  
## <a name="implementing-signature-help-signatures-and-parameters"></a>Implementando assinaturas e parâmetros de ajuda de assinatura  
 A fonte de ajuda da assinatura é baseada em assinaturas que implementam <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> , cada uma delas contendo parâmetros que implementam <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> . Em uma implementação completa, essas informações seriam obtidas na documentação do idioma, mas neste exemplo, as assinaturas são embutidas em código.  
  
#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar a assinatura ajuda de assinaturas e parâmetros  
  
1. Adicione um arquivo de classe e nomeie-o `SignatureHelpSource` .  
  
2. Adicione as seguintes importações.  
  
     [!code-csharp[VSSDKSignatureHelpTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#1)]
     [!code-vb[VSSDKSignatureHelpTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#1)]  
  
3. Adicione uma classe chamada `TestParameter` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#2)]
     [!code-vb[VSSDKSignatureHelpTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#2)]  
  
4. Adicione um construtor que define todas as propriedades.  
  
     [!code-csharp[VSSDKSignatureHelpTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#3)]
     [!code-vb[VSSDKSignatureHelpTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#3)]  
  
5. Adicione as propriedades de <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#4)]
     [!code-vb[VSSDKSignatureHelpTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#4)]  
  
6. Adicione uma classe chamada `TestSignature` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#5)]
     [!code-vb[VSSDKSignatureHelpTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#5)]  
  
7. Adicione alguns campos particulares.  
  
     [!code-csharp[VSSDKSignatureHelpTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#6)]
     [!code-vb[VSSDKSignatureHelpTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#6)]  
  
8. Adicione um construtor que defina os campos e assine o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKSignatureHelpTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#7)]
     [!code-vb[VSSDKSignatureHelpTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#7)]  
  
9. Declare um `CurrentParameterChanged` evento. Esse evento é gerado quando o usuário preenche um dos parâmetros na assinatura.  
  
     [!code-csharp[VSSDKSignatureHelpTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#8)]
     [!code-vb[VSSDKSignatureHelpTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#8)]  
  
10. Implemente a <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> propriedade para que ela gere o `CurrentParameterChanged` evento quando o valor da propriedade for alterado.  
  
     [!code-csharp[VSSDKSignatureHelpTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#9)]
     [!code-vb[VSSDKSignatureHelpTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#9)]  
  
11. Adicione um método que gera o `CurrentParameterChanged` evento.  
  
     [!code-csharp[VSSDKSignatureHelpTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#10)]
     [!code-vb[VSSDKSignatureHelpTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#10)]  
  
12. Adicione um método que computa o parâmetro atual comparando o número de vírgulas no <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> para o número de vírgulas na assinatura.  
  
     [!code-csharp[VSSDKSignatureHelpTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#11)]
     [!code-vb[VSSDKSignatureHelpTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#11)]  
  
13. Adicione um manipulador de eventos para o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento que chama o `ComputeCurrentParameter()` método.  
  
     [!code-csharp[VSSDKSignatureHelpTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#12)]
     [!code-vb[VSSDKSignatureHelpTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#12)]  
  
14. Implemente a propriedade <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Essa propriedade contém um <xref:Microsoft.VisualStudio.Text.ITrackingSpan> que corresponde ao intervalo de texto no buffer ao qual a assinatura se aplica.  
  
     [!code-csharp[VSSDKSignatureHelpTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#13)]
     [!code-vb[VSSDKSignatureHelpTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#13)]  
  
15. Implemente os outros parâmetros.  
  
     [!code-csharp[VSSDKSignatureHelpTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#14)]
     [!code-vb[VSSDKSignatureHelpTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#14)]  
  
## <a name="implementing-the-signature-help-source"></a>Implementando a fonte de ajuda da assinatura  
 A fonte de ajuda da assinatura é o conjunto de assinaturas para as quais você fornece informações.  
  
#### <a name="to-implement-the-signature-help-source"></a>Para implementar a fonte de ajuda da assinatura  
  
1. Adicione uma classe chamada `TestSignatureHelpSource` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#15)]
     [!code-vb[VSSDKSignatureHelpTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#15)]  
  
2. Adicione uma referência ao buffer de texto.  
  
     [!code-csharp[VSSDKSignatureHelpTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#16)]
     [!code-vb[VSSDKSignatureHelpTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#16)]  
  
3. Adicione um construtor que defina o buffer de texto e o provedor de origem de ajuda de assinatura.  
  
     [!code-csharp[VSSDKSignatureHelpTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#17)]
     [!code-vb[VSSDKSignatureHelpTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#17)]  
  
4. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> . Neste exemplo, as assinaturas são embutidas em código, mas em uma implementação completa, você obteria essas informações da documentação do idioma.  
  
     [!code-csharp[VSSDKSignatureHelpTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#18)]
     [!code-vb[VSSDKSignatureHelpTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#18)]  
  
5. O método auxiliar `CreateSignature()` é fornecido apenas para ilustração.  
  
     [!code-csharp[VSSDKSignatureHelpTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#19)]
     [!code-vb[VSSDKSignatureHelpTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#19)]  
  
6. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> . Neste exemplo, há apenas duas assinaturas, cada uma delas tem dois parâmetros. Portanto, esse método não é necessário. Em uma implementação mais completa, na qual mais de uma fonte de ajuda de assinatura está disponível, esse método é usado para decidir se a fonte de ajuda de assinatura de prioridade mais alta pode fornecer uma assinatura correspondente. Se não puder, o método retornará NULL e a fonte Next-mais alta-Priority será solicitada a fornecer uma correspondência.  
  
     [!code-csharp[VSSDKSignatureHelpTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#20)]
     [!code-vb[VSSDKSignatureHelpTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#20)]  
  
7. Implemente o método Dispose ():  
  
     [!code-csharp[VSSDKSignatureHelpTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#21)]
     [!code-vb[VSSDKSignatureHelpTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#21)]  
  
## <a name="implementing-the-signature-help-source-provider"></a>Implementando o provedor de origem de ajuda de assinatura  
 O provedor de origem de ajuda de assinatura é responsável por exportar a parte do componente Managed Extensibility Framework (MEF) e para instanciar a fonte de ajuda da assinatura.  
  
#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar o provedor de origem de ajuda de assinatura  
  
1. Adicione uma classe chamada `TestSignatureHelpSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> e exporte-a com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto" e um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes = "padrão".  
  
     [!code-csharp[VSSDKSignatureHelpTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#22)]
     [!code-vb[VSSDKSignatureHelpTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#22)]  
  
2. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> ao instanciar o `TestSignatureHelpSource` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#23)]
     [!code-vb[VSSDKSignatureHelpTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#23)]  
  
## <a name="implementing-the-command-handler"></a>Implementando o manipulador de comandos  
 A ajuda da assinatura é normalmente disparada por um caractere (caractere e descartado por um). Você pode lidar com esses pressionamentos de teclas implementando um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para que ele dispare uma sessão de ajuda de assinatura quando recebe um caractere (precedido por um nome de método conhecido e ignora a sessão quando recebe um).  
  
#### <a name="to-implement-the-command-handler"></a>Para implementar o manipulador de comandos  
  
1. Adicione uma classe chamada `TestSignatureHelpCommand` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#24)]
     [!code-vb[VSSDKSignatureHelpTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#24)]  
  
2. Adicione campos particulares para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que permite que você adicione o manipulador de comandos à cadeia de manipuladores de comandos), a exibição de texto, a assinatura, o agente de ajuda e a sessão, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> e a próxima <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#25)]
     [!code-vb[VSSDKSignatureHelpTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#25)]  
  
3. Adicione um construtor para inicializar esses campos e adicionar o filtro de comando à cadeia de filtros de comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#26)]
     [!code-vb[VSSDKSignatureHelpTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#26)]  
  
4. Implemente o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para disparar a sessão de ajuda de assinatura quando o filtro de comando receber um (caractere após um dos nomes de método conhecidos e para ignorar a sessão quando receber um), enquanto a sessão ainda está ativa. Em todos os casos, o comando é encaminhado.  
  
     [!code-csharp[VSSDKSignatureHelpTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#27)]
     [!code-vb[VSSDKSignatureHelpTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#27)]  
  
5. Implemente o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para que ele sempre encaminhe o comando.  
  
     [!code-csharp[VSSDKSignatureHelpTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#28)]
     [!code-vb[VSSDKSignatureHelpTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#28)]  
  
## <a name="implementing-the-signature-help-command-provider"></a>Implementando o provedor de comando de ajuda de assinatura  
 Você pode fornecer o comando de ajuda de assinatura implementando o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> para instanciar o manipulador de comandos quando a exibição de texto for criada.  
  
#### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar o provedor de comandos de ajuda de assinatura  
  
1. Adicione uma classe chamada `TestSignatureHelpController` que implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> e exporte-a com o <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , o <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> e o <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> .  
  
     [!code-csharp[VSSDKSignatureHelpTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#29)]
     [!code-vb[VSSDKSignatureHelpTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#29)]  
  
2. Importe o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> (usado para obter o <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , dado o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto), o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> (usado para localizar a palavra atual) e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> (para disparar a sessão de ajuda da assinatura).  
  
     [!code-csharp[VSSDKSignatureHelpTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#30)]
     [!code-vb[VSSDKSignatureHelpTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#30)]  
  
3. Implemente o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método instanciando o `TestSignatureCommandHandler` .  
  
     [!code-csharp[VSSDKSignatureHelpTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdksignaturehelptest/cs/signaturehelpsource.cs#31)]
     [!code-vb[VSSDKSignatureHelpTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksignaturehelptest/vb/signaturehelpsource.vb#31)]  
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
 Para testar esse código, crie a solução SignatureHelpTest e execute-a na instância experimental.  
  
#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para compilar e testar a solução SignatureHelpTest  
  
1. Compile a solução.  
  
2. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3. Crie um arquivo de texto e digite algum texto que inclua a palavra "Adicionar", além de um parêntese de abertura.  
  
4. Depois de digitar o parêntese de abertura, você deverá ver uma dica de ferramenta que exibe uma lista das duas assinaturas do `add()` método.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
