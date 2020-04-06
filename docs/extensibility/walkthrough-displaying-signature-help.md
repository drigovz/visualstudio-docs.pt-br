---
title: 'Passo a passo: Exibindo ajuda de assinatura | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - signature help/parameter info
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85d7eb3959064468e7583ec0c8a927f3e139daf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697427"
---
# <a name="walkthrough-display-signature-help"></a>Passo a passo: Ajuda de assinatura de exibição
Signature Help (também conhecido como *Parameter Info)* exibe a assinatura de um método em uma dica de ferramenta quando um usuário digita o caractere iniciar da lista de parâmetros (tipicamente um parêntese de abertura). Como um parâmetro e um separador de parâmetros (tipicamente uma comma) são digitados, a dica de ferramenta é atualizada para mostrar o próximo parâmetro em negrito. Você pode definir a Ajuda de Assinatura das seguintes maneiras: no contexto de um serviço de idioma, defina a extensão do seu próprio nome de arquivo e o tipo de conteúdo e exiba ajuda de assinatura para esse tipo, ou exiba Ajuda de Assinatura para um tipo de conteúdo existente (por exemplo, "texto"). Este passo a passo mostra como exibir a Ajuda de Assinatura para o tipo de conteúdo "texto".

 A Signature Help é normalmente acionada digitando um caractere específico, por exemplo, "(" (abertura de parênteses) e descartada digitando outro caractere, por exemplo, ")" (fechando parênteses). Os recursos do IntelliSense que são acionados digitando um caractere podem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ser implementados usando um manipulador <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> de comando para as teclas (a interface) e um provedor manipulador que implementa a interface. Para criar a fonte de Ajuda de Assinatura, que é <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> a lista de assinaturas <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> que participam do Signature Help, implemente a interface e um provedor de origem que execute a interface. Os provedores são partes componentes do Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada) e são responsáveis por exportar as classes de origem e controladore importar serviços e corretores, por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite navegar no buffer de texto, e o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, que aciona a sessão De Ajuda de Assinatura.

 Este passo a passo mostra como configurar a Signature Help para um conjunto de identificadores codificados. Em implementações completas, o idioma é responsável por fornecer esse conteúdo.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-mef-project"></a>Criando um projeto MEF

#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `SignatureHelpTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

4. Adicione as seguintes referências ao projeto e certifique-se de que **o CopyLocal** está definido como `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.shell.14.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-signature-help-signatures-and-parameters"></a>Implementar assinaturas e parâmetros de ajuda de assinatura
 A fonte signature help baseia-se em assinaturas que <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature> <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>implementam , cada uma das quais contém parâmetros que implementam . Em uma implementação completa, essas informações seriam obtidas a partir da documentação do idioma, mas neste exemplo, as assinaturas são codificadas.

#### <a name="to-implement-the-signature-help-signatures-and-parameters"></a>Para implementar as assinaturas e parâmetros de ajuda de assinatura

1. Adicione um arquivo de `SignatureHelpSource`classe e nomeie-o .

2. Adicione as seguintes importações.

     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]

3. Adicione uma `TestParameter` classe nomeada <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>que implementa .

     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]

4. Adicione um construtor que define todas as propriedades.

     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]

5. Adicione as <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>propriedades de .

     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]

6. Adicione uma `TestSignature` classe nomeada <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>que implementa .

     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]

7. Adicione alguns campos privados.

     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]

8. Adicione um construtor que define os campos <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> e assina o evento.

     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]

9. Declare `CurrentParameterChanged` um evento. Este evento é levantado quando o usuário preenche um dos parâmetros da assinatura.

     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]

10. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> a propriedade para `CurrentParameterChanged` que eleve o evento quando o valor do imóvel for alterado.

     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]

11. Adicione um método `CurrentParameterChanged` que eleve o evento.

     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]

12. Adicione um método que calcule o parâmetro atual comparando o <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> número de commas no número de commas na assinatura.

     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]

13. Adicione um manipulador <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> de eventos `ComputeCurrentParameter()` para o evento que chama o método.

     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]

14. Implemente a propriedade <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Esta propriedade <xref:Microsoft.VisualStudio.Text.ITrackingSpan> contém um que corresponde ao período de texto no buffer ao qual a assinatura se aplica.

     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]

15. Implemente os outros parâmetros.

     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]

## <a name="implement-the-signature-help-source"></a>Implementar a fonte de ajuda de assinatura
 A fonte de ajuda de assinatura é o conjunto de assinaturas para as quais você fornece informações.

#### <a name="to-implement-the-signature-help-source"></a>Para implementar a fonte de ajuda de assinatura

1. Adicione uma `TestSignatureHelpSource` classe nomeada <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>que implementa .

     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]

2. Adicione uma referência ao buffer de texto.

     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]

3. Adicione um construtor que define o buffer de texto e o provedor de origem de ajuda de assinatura.

     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]

4. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A> . Neste exemplo, as assinaturas são codificadas, mas em uma implementação completa você obteria essas informações da documentação do idioma.

     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]

5. O método `CreateSignature()` auxiliar é fornecido apenas para ilustração.

     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]

6. Implementar o método de <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A> . Neste exemplo, há apenas duas assinaturas, cada uma com dois parâmetros. Portanto, este método não é necessário. Em uma implementação mais completa, na qual mais de uma fonte de Ajuda de Assinatura está disponível, este método é usado para decidir se a fonte de ajuda de assinatura de maior prioridade pode fornecer uma assinatura correspondente. Se não puder, o método retorna nulo e a próxima fonte de maior prioridade é solicitada a fornecer uma correspondência.

     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]

7. Implementar `Dispose()` o método:

     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]

## <a name="implement-the-signature-help-source-provider"></a>Implementar o provedor de origem de ajuda de assinatura
 O provedor de origem de ajuda de assinatura é responsável por exportar a parte do componente MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada) e por instanciar a fonte de Ajuda de Assinatura.

#### <a name="to-implement-the-signature-help-source-provider"></a>Para implementar o provedor de origem de ajuda de assinatura

1. Adicione uma `TestSignatureHelpSourceProvider` classe nomeada <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>que implementa <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> e exporte-a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> com um , um de "texto", e um de Antes="padrão".

     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]

2. Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> instanciando `TestSignatureHelpSource`o .

     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]

## <a name="implement-the-command-handler"></a>Implementar o manipulador de comando
 Signature Help é normalmente acionado por um caractere de abertura de parênteses "(" e rejeitado por um caractere de parêntese sumário ")". Você pode lidar com esses <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pressionamentos de teclas executando um para que ele acione uma sessão de Ajuda de Assinatura quando recebe um caractere de parênteses de abertura precedido por um nome de método conhecido e descarta a sessão quando recebe um caractere de parêntese de fechamento.

#### <a name="to-implement-the-command-handler"></a>Para implementar o manipulador de comando

1. Adicione uma `TestSignatureHelpCommand` classe nomeada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>que implementa .

     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]

2. Adicione campos privados para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adaptador (que permite adicionar o manipulador de comando à cadeia de manipuladores de comando), a exibição de texto, o corretor de ajuda de assinatura e a sessão, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, e o próximo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]

3. Adicione um construtor para inicializar esses campos e adicionar o filtro de comando à cadeia de filtros de comando.

     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]

4. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> o método para ativar a sessão De ajuda de assinatura quando o filtro de comando receber um caractere de parêntese de abertura "(" após um dos nomes de método conhecidos e para descartar a sessão quando receber um caractere de entreparênte de fechamento ")" enquanto a sessão ainda estiver ativa. Em todos os casos, o comando é encaminhado.

     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]

5. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> o método para que ele sempre encaminhe o comando.

     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]

## <a name="implement-the-signature-help-command-provider"></a>Implementar o provedor de comando Signature Help
 Você pode fornecer o comando Ajuda <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> de assinatura implementando o para instanciar o manipulador de comando quando a exibição de texto for criada.

### <a name="to-implement-the-signature-help-command-provider"></a>Para implementar o provedor de comando Signature Help

1. Adicione uma `TestSignatureHelpController` classe nomeada <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> que implemente <xref:Microsoft.VisualStudio.Utilities.NameAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>exporte-a com o , e .

     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]

2. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> o (usado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obter o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , dado o objeto), <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> o (usado para encontrar a palavra atual) e o (para acionar a sessão De ajuda de assinatura).

     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]

3. Implementar <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> o método instanciando o `TestSignatureCommandHandler`.

     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-csharp[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]

## <a name="build-and-test-the-code"></a>Construir e testar o código
 Para testar esse código, crie a solução SignatureHelpTest e execute-o na instância experimental.

#### <a name="to-build-and-test-the-signaturehelptest-solution"></a>Para construir e testar a solução SignatureHelpTest

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto que inclua a palavra "adicionar" mais um parêntese de abertura.

4. Depois de digitar o parêntese de abertura, você deve ver uma `add()` dica de ferramenta que exibe uma lista das duas assinaturas para o método.

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
