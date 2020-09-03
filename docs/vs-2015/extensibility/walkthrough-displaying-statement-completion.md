---
title: 'Walkthrough: exibindo a conclusão da instrução | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db4e63beb1e3d4ff53e547492ae9eae7ee8001e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202008"
---
# <a name="walkthrough-displaying-statement-completion"></a>Passo a passo: exibindo o preenchimento de declaração
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode implementar a conclusão da instrução baseada em linguagem definindo os identificadores para os quais você deseja fornecer a conclusão e, em seguida, disparando uma sessão de conclusão. Você pode definir a conclusão da instrução no contexto de um serviço de idioma, definir sua própria extensão de nome de arquivo e tipo de conteúdo e, em seguida, exibir a conclusão apenas para esse tipo, ou pode disparar a conclusão para um tipo de conteúdo existente — por exemplo, "texto sem formatação". Este tutorial mostra como disparar a conclusão da instrução para o tipo de conteúdo "texto não criptografado", que é o tipo de conteúdo dos arquivos de texto. O tipo de conteúdo "text" é o ancestral de todos os outros tipos de conteúdo, incluindo arquivos de código e XML.  
  
 A conclusão da instrução é normalmente disparada digitando-se determinados caracteres — por exemplo, digitando o início de um identificador, como "usando". Normalmente, ele é Descartado pressionando-se a barra de espaços, a guia ou a tecla Enter para confirmar uma seleção. Você pode implementar os recursos do IntelliSense que são disparados digitando um caractere usando um manipulador de comando para os pressionamentos de tecla (a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface) e um provedor de manipulador que implementa a <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interface. Para criar a origem de conclusão, que é a lista de identificadores que participam da conclusão, implemente a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interface e um provedor de origem de conclusão (a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface). Os provedores são partes de componente Managed Extensibility Framework (MEF). Eles são responsáveis por exportar as classes de origem e controlador e importar serviços e agentes — por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que permite a navegação no buffer de texto e o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> , que dispara a sessão de conclusão.  
  
 Este tutorial mostra como implementar a conclusão de uma instrução para um conjunto embutido de identificadores. Em implementações completas, o serviço de idioma e a documentação do idioma são responsáveis por fornecer esse conteúdo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto do MEF  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto do MEF  
  
1. Crie um projeto VSIX em C#. (Na caixa de diálogo **novo projeto** , selecione **Visual C#/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `CompletionTest` .  
  
2. Adicione um modelo de item de classificação do editor ao projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Exclua os arquivos de classe existentes.  
  
4. Adicione as seguintes referências ao projeto e verifique se **CopyLocal** está definido como `false` :  
  
     Microsoft. VisualStudio. editor  
  
     Microsoft. VisualStudio. Language. IntelliSense  
  
     Microsoft. VisualStudio. OLE. Interop  
  
     Microsoft. VisualStudio. Shell. 14.0  
  
     Microsoft. VisualStudio. Shell. imutável. 10.0  
  
     Microsoft. VisualStudio. Textmanager. Interop  
  
## <a name="implementing-the-completion-source"></a>Implementando a origem de conclusão  
 A fonte de conclusão é responsável por coletar o conjunto de identificadores e adicionar o conteúdo à janela de conclusão quando um usuário digita um gatilho de conclusão, como as primeiras letras de um identificador. Neste exemplo, os identificadores e suas descrições são embutidos em código no <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método. Na maioria dos usos do mundo real, você usaria o analisador de seu idioma para obter os tokens para preencher a lista de conclusão.  
  
#### <a name="to-implement-the-completion-source"></a>Para implementar a origem de conclusão  
  
1. Adicione um arquivo de classe e nomeie-o `TestCompletionSource` .  
  
2. Adicione estas importações:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3. Modifique a declaração de classe para `TestCompletionSource` que ela implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> :  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4. Adicione campos particulares para o provedor de origem, o buffer de texto e uma lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que correspondem aos identificadores que participarão da sessão de conclusão):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5. Adicione um construtor que define o provedor de origem e o buffer. A `TestCompletionSourceProvider` classe é definida em etapas posteriores:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6. Implemente o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> método adicionando um conjunto de conclusão que contenha as conclusões que você deseja fornecer no contexto. Cada conjunto de conclusão contém um conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> conclusões e corresponde a uma guia da janela de conclusão. (Em projetos Visual Basic, as guias de janela de conclusão são nomeadas como **comuns** e **todas**.) O método FindTokenSpanAtPosition é definido na próxima etapa.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7. O método a seguir é usado para localizar a palavra atual da posição do cursor:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8. Implemente o `Dispose()` método:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Implementando o provedor de origem de conclusão  
 O provedor de origem de conclusão é a parte do componente do MEF que instancia a origem de conclusão.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Para implementar o provedor de origem de conclusão  
  
1. Adicione uma classe chamada `TestCompletionSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> . Exporte essa classe com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "texto sem formatação" e uma <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "conclusão do teste".  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2. Importar um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> , que é usado para localizar a palavra atual na fonte de conclusão.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3. Implemente o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> método para instanciar a origem de conclusão.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Implementando o provedor do manipulador de comandos de conclusão  
 O provedor do manipulador de comandos de conclusão é derivado de a <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> , que escuta um evento de criação de exibição de texto e converte a exibição de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> — que permite a adição do comando à cadeia de comandos do shell do Visual Studio — a um <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Como essa classe é uma exportação de MEF, você também pode usá-la para importar os serviços exigidos pelo próprio manipulador de comandos.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar o provedor do manipulador de comandos de conclusão  
  
1. Adicione um arquivo chamado `TestCompletionCommandHandler` .  
  
2. Adicione estas instruções using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3. Adicione uma classe chamada `TestCompletionHandlerProvider` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> . Exporte essa classe com um <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "manipulador de conclusão de token", um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto sem formatação" e um <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable> .  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4. Importe o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , que permite a conversão de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para um <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , um <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> e um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que habilita o acesso aos serviços padrão do Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5. Implemente o <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> método para instanciar o manipulador de comandos.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Implementando o manipulador de comandos de conclusão  
 Como a conclusão da instrução é disparada por pressionamentos de teclas, você deve implementar a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface para receber e processar os pressionamentos de teclas que disparam, confirmam e descartam a sessão de conclusão.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Para implementar o manipulador de comando de conclusão  
  
1. Adicione uma classe chamada `TestCompletionCommandHandler` que implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> :  
  
    [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
    [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2. Adicione campos particulares para o próximo manipulador de comandos (para o qual você passa o comando), a exibição de texto, o provedor de manipulador de comandos (que permite o acesso a vários serviços) e uma sessão de conclusão:  
  
    [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
    [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3. Adicione um construtor que defina a exibição de texto e os campos de provedor e adicione o comando à cadeia de comandos:  
  
    [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
    [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4. Implemente o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método passando o comando ao longo de:  
  
    [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
    [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5. Implementar o método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Quando esse método recebe um pressionamento de tecla, ele deve executar uma destas ações:  
  
   - Permitir que o caractere seja gravado no buffer e, em seguida, disparar ou filtrar a conclusão. (Imprimir caracteres faça isso.)  
  
   - Confirme a conclusão, mas não permita que o caractere seja gravado no buffer. (Espaço em branco, guia e digite fazer isso quando uma sessão de conclusão for exibida.)  
  
   - Permitir que o comando seja passado para o próximo manipulador. (Todos os outros comandos).  
  
     Como esse método pode exibir a interface do usuário, chame para certificar-se de <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> que ele não seja chamado em um contexto de automação:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6. Esse código é um método particular que dispara a sessão de conclusão:  
  
    [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
    [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7. O exemplo a seguir é um método particular que cancela a assinatura do <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:  
  
    [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
    [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Criando e testando o código  
 Para testar esse código, crie a solução CompletionTest e execute-a na instância experimental.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar e testar a solução CompletionTest  
  
1. Compile a solução.  
  
2. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3. Crie um arquivo de texto e digite algum texto que inclua a palavra "Adicionar".  
  
4. Conforme você digita o primeiro "a" e, em seguida, "d", uma lista que contém "adição" e "adaptação" deve ser exibida. Observe que a adição está selecionada. Quando você digita outro "d", a lista deve conter apenas "adição", que agora é selecionada. Você pode confirmar "adição" pressionando a barra de espaços, a guia ou a tecla Enter, ou descartar a lista digitando ESC ou qualquer outra chave.  
  
## <a name="see-also"></a>Consulte Também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
