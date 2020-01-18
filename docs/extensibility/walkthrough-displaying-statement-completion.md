---
title: 'Walkthrough: exibindo a conclusão da instrução | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: madskristensen
ms.author: madsk
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 78cbcc9b2efd37aa99906d7ed7708621ec213b2e
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269074"
---
# <a name="walkthrough-display-statement-completion"></a>Walkthrough: exibir a conclusão da instrução
Você pode implementar a conclusão da instrução baseada em linguagem definindo os identificadores para os quais você deseja fornecer a conclusão e, em seguida, disparando uma sessão de conclusão. Você pode definir a conclusão da instrução no contexto de um serviço de idioma, definir sua própria extensão de nome de arquivo e tipo de conteúdo e, em seguida, exibir a conclusão apenas para esse tipo. Ou, você pode disparar a conclusão para um tipo de conteúdo existente — por exemplo, "texto sem formatação". Este tutorial mostra como disparar a conclusão da instrução para o tipo de conteúdo "texto não criptografado", que é o tipo de conteúdo dos arquivos de texto. O tipo de conteúdo "text" é o ancestral de todos os outros tipos de conteúdo, incluindo arquivos de código e XML.

 A conclusão da instrução é normalmente disparada digitando-se determinados caracteres — por exemplo, digitando o início de um identificador, como "usando". Normalmente, é Descartado pressionando-se a **barra de espaços**, a **guia**ou a tecla **Enter** para confirmar uma seleção. Você pode implementar os recursos do IntelliSense que disparam ao digitar um caractere usando um manipulador de comando para os pressionamentos de tecla (a interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) e um provedor de manipulador que implementa a interface <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Para criar a origem de conclusão, que é a lista de identificadores que participam da conclusão, implemente a interface de <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> e um provedor de origem de conclusão (a interface <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>). Os provedores são partes de componente Managed Extensibility Framework (MEF). Eles são responsáveis por exportar as classes de origem e controlador e importar serviços e agentes — por exemplo, o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que permite a navegação no buffer de texto e o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, que dispara a sessão de conclusão.

 Este tutorial mostra como implementar a conclusão de uma instrução para um conjunto embutido de identificadores. Em implementações completas, o serviço de idioma e a documentação do idioma são responsáveis por fornecer esse conteúdo.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio do centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Criar um projeto do MEF

#### <a name="to-create-a-mef-project"></a>Para criar um projeto do MEF

1. Crie um C# projeto VSIX. (Na caixa de diálogo **novo projeto** , **selecione C# Visual/extensibilidade**e, em seguida, **projeto VSIX**.) Nomeie a solução `CompletionTest`.

2. Adicione um modelo de item de classificação do editor ao projeto. Para obter mais informações, consulte [criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

4. Adicione as seguintes referências ao projeto e verifique se **CopyLocal** está definido como `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft. VisualStudio. Shell. 15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementar a origem de conclusão
 A fonte de conclusão é responsável por coletar o conjunto de identificadores e adicionar o conteúdo à janela de conclusão quando um usuário digita um gatilho de conclusão, como as primeiras letras de um identificador. Neste exemplo, os identificadores e suas descrições são embutidos em código no método <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A>. Na maioria dos usos do mundo real, você usaria o analisador de seu idioma para obter os tokens para preencher a lista de conclusão.

### <a name="to-implement-the-completion-source"></a>Para implementar a origem de conclusão

1. Adicione um arquivo de classe e nomeie-o `TestCompletionSource`.

2. Adicione estas importações:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modifique a declaração de classe para `TestCompletionSource` para que ela implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Adicione campos particulares para o provedor de origem, o buffer de texto e uma lista de objetos de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (que correspondem aos identificadores que participarão da sessão de conclusão):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Adicione um construtor que define o provedor de origem e o buffer. A classe `TestCompletionSourceProvider` é definida em etapas posteriores:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implemente o método <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> adicionando um conjunto de conclusão que contenha as conclusões que você deseja fornecer no contexto. Cada conjunto de conclusão contém um conjunto de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> conclusões e corresponde a uma guia da janela de conclusão. (Em projetos Visual Basic, as guias de janela de conclusão são nomeadas como **comuns** e **todas**.) O método `FindTokenSpanAtPosition` é definido na próxima etapa.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. O método a seguir é usado para localizar a palavra atual da posição do cursor:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implemente o método `Dispose()`:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementar o provedor de origem de conclusão
 O provedor de origem de conclusão é a parte do componente do MEF que instancia a origem de conclusão.

### <a name="to-implement-the-completion-source-provider"></a>Para implementar o provedor de origem de conclusão

1. Adicione uma classe chamada `TestCompletionSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Exporte essa classe com uma <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto sem formatação" e uma <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "conclusão do teste".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importar um <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, que localiza a palavra atual na fonte de conclusão.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implemente o método <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> para instanciar a origem de conclusão.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementar o provedor do manipulador de comandos de conclusão
 O provedor do manipulador de comandos de conclusão é derivado de um <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, que escuta um evento de criação de exibição de texto e converte a exibição de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— que permite a adição do comando à cadeia de comandos do shell do Visual Studio — a um <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Como essa classe é uma exportação de MEF, você também pode usá-la para importar os serviços exigidos pelo próprio manipulador de comandos.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar o provedor do manipulador de comandos de conclusão

1. Adicione um arquivo chamado `TestCompletionCommandHandler`.

2. Adicione-as usando as diretivas:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Adicione uma classe chamada `TestCompletionHandlerProvider` que implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Exporte essa classe com uma <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "manipulador de conclusão de token", uma <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto sem formatação" e uma <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importe o <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, que permite a conversão de um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> em um <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, um <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>e um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> que permite o acesso aos serviços padrão do Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implemente o método <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> para instanciar o manipulador de comandos.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementar o manipulador de comandos de conclusão
 Como a conclusão da instrução é disparada por pressionamentos de teclas, você deve implementar a interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para receber e processar os pressionamentos de teclas que disparam, confirmam e descartam a sessão de conclusão.

#### <a name="to-implement-the-completion-command-handler"></a>Para implementar o manipulador de comando de conclusão

1. Adicione uma classe chamada `TestCompletionCommandHandler` que implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Adicione campos particulares para o próximo manipulador de comandos (para o qual você passa o comando), a exibição de texto, o provedor de manipulador de comandos (que permite o acesso a vários serviços) e uma sessão de conclusão:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Adicione um construtor que defina a exibição de texto e os campos de provedor e adicione o comando à cadeia de comandos:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implemente o método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> passando o comando ao longo de:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementar o método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Quando esse método recebe um pressionamento de tecla, ele deve executar uma destas ações:

   - Permitir que o caractere seja gravado no buffer e, em seguida, disparar ou filtrar a conclusão. (Imprimir caracteres faça isso.)

   - Confirme a conclusão, mas não permita que o caractere seja gravado no buffer. (Espaço em branco, **guia**e **digite** fazer isso quando uma sessão de conclusão for exibida.)

   - Permitir que o comando seja passado para o próximo manipulador. (Todos os outros comandos).

     Como esse método pode exibir a interface do usuário, chame <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> para certificar-se de que ele não seja chamado em um contexto de automação:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Esse código é um método particular que dispara a sessão de conclusão:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. O exemplo a seguir é um método particular que cancela a assinatura do evento <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed>:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Compilar e testar o código
 Para testar esse código, crie a solução CompletionTest e execute-a na instância experimental.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Para compilar e testar a solução CompletionTest

1. {1&gt;Compile a solução.&lt;1}

2. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto que inclua a palavra "Adicionar".

4. Conforme você digita o primeiro "a" e, em seguida, "d", uma lista que contém "adição" e "adaptação" deve aparecer. Observe que a adição está selecionada. Quando você digita outro "d", a lista deve conter apenas "adição", que agora é selecionada. Você pode confirmar "adição" pressionando a **barra de espaços**, a **guia**ou a tecla **Enter** , ou descartar a lista digitando ESC ou qualquer outra chave.

## <a name="see-also"></a>Veja também
- [Walkthrough: vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
