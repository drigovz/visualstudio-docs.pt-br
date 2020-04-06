---
title: 'Passo a passo: Exibindo a conclusão da declaração | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697409"
---
# <a name="walkthrough-display-statement-completion"></a>Passo a passo: exibir preenchimento de declaração
Você pode implementar a conclusão da declaração baseada em idioma definindo os identificadores para os quais deseja fornecer conclusão e, em seguida, desencadeando uma sessão de conclusão. Você pode definir a conclusão da declaração no contexto de um serviço de idioma, definir a extensão e o tipo de conteúdo do seu próprio nome de arquivo e, em seguida, exibir a conclusão para esse tipo. Ou, você pode ativar a conclusão de um tipo de conteúdo existente — por exemplo, "plaintext". Este passo a passo mostra como ativar a conclusão da declaração para o tipo de conteúdo "plaintext", que é o tipo de conteúdo dos arquivos de texto. O tipo de conteúdo "texto" é o ancestral de todos os outros tipos de conteúdo, incluindo código e arquivos XML.

 A conclusão da declaração é normalmente desencadeada digitando certos caracteres — por exemplo, digitando o início de um identificador como "usar". É normalmente descartado pressionando a **tecla Spacebar**, **Tab**ou **Enter** para cometer uma seleção. Você pode implementar os recursos do IntelliSense que disparam ao digitar um <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> caractere usando um manipulador de <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> comando para as teclas (a interface) e um provedor de manipulador que implementa a interface. Para criar a fonte de conclusão, que é a lista <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> de identificadores que <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> participam da conclusão, implemente a interface e um provedor de fonte de conclusão (a interface). Os provedores são partes componentes do Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada). Eles são responsáveis por exportar as classes de origem e controlador e <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>importar serviços e corretores — <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>por exemplo, o , que permite a navegação no buffer de texto, e o , que desencadeia a sessão de conclusão.

 Este passo a passo mostra como implementar a conclusão da declaração para um conjunto de identificadores codificados. Em implementações completas, o serviço de idiomas e a documentação do idioma são responsáveis por fornecer esse conteúdo.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Criar um Projeto MEF

#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF

1. Crie um projeto C# VSIX. (Na caixa de diálogo **Novo Projeto,** selecione **Visual C# / Extensibility**, em seguida, **Projeto VSIX**.) Diga a `CompletionTest`solução.

2. Adicione um modelo de item do Editor Classifier ao projeto. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Exclua os arquivos de classe existentes.

4. Adicione as seguintes referências ao projeto e certifique-se de que **o CopyLocal** está definido como `false`:

     Microsoft.VisualStudio.Editor

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.shell.15.0

     Microsoft.VisualStudio.Shell.Immutável.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Implementar a fonte de conclusão
 A fonte de conclusão é responsável por coletar o conjunto de identificadores e adicionar o conteúdo à janela de conclusão quando um usuário digita um gatilho de conclusão, como as primeiras letras de um identificador. Neste exemplo, os identificadores e suas descrições são <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> codificados no método. Na maioria dos usos do mundo real, você usaria o analisador do seu idioma para obter os tokens para preencher a lista de conclusão.

### <a name="to-implement-the-completion-source"></a>Para implementar a fonte de conclusão

1. Adicione um arquivo de `TestCompletionSource`classe e nomeie-o .

2. Adicione essas importações:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Modifique a `TestCompletionSource` declaração de classe <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>para que ela implemente:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Adicione campos privados para o provedor de origem, o buffer de texto e uma lista de <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> objetos (que correspondem aos identificadores que participarão da sessão de conclusão):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Adicione um construtor que define o provedor de origem e o buffer. A `TestCompletionSourceProvider` classe é definida em etapas posteriores:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> o método adicionando um conjunto de conclusão que contenha as conclusões que você deseja fornecer no contexto. Cada conjunto de conclusão <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> contém um conjunto de conclusões e corresponde a uma guia da janela de conclusão. (Em projetos Visual Basic, as guias de janela de conclusão são nomeadas **Comum** e **Tudo**.) O `FindTokenSpanAtPosition` método é definido na próxima etapa.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. O seguinte método é usado para encontrar a palavra atual da posição do cursor:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Implementar `Dispose()` o método:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Implementar o provedor de fonte de conclusão
 O provedor de fonte de conclusão é a parte componente MEF que instancia a fonte de conclusão.

### <a name="to-implement-the-completion-source-provider"></a>Para implementar o provedor de fonte de conclusão

1. Adicione uma `TestCompletionSourceProvider` classe nomeada <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>que implementa . Exporte esta <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> classe com um de <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "texto simples" e um de "conclusão de teste".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Importe <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>a , que encontra a palavra atual na fonte de conclusão.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> o método para instanciar a fonte de conclusão.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Implementar o provedor de manipulador de comando de conclusão
 O provedor de manipulador de <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>comando de conclusão é derivado de um , que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ouve um evento de criação de exibição de texto <xref:Microsoft.VisualStudio.Text.Editor.ITextView>e converte a exibição de um — que permite a adição do comando à cadeia de comando do shell do Visual Studio — a um . Como esta classe é uma exportação MEF, você também pode usá-la para importar os serviços que são exigidos pelo próprio manipulador de comandos.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Para implementar o provedor de manipulador de comando de conclusão

1. Adicione um `TestCompletionCommandHandler`arquivo chamado .

2. Adicione estas diretivas usando:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Adicione uma `TestCompletionHandlerProvider` classe nomeada <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>que implementa . Exporte esta <xref:Microsoft.VisualStudio.Utilities.NameAttribute> classe com um de <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "manipulador de conclusão <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> de <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>token", um de "plaintext", e um de .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Importe <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>o , que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> permite <xref:Microsoft.VisualStudio.Text.Editor.ITextView>a <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>conversão <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> de a, a , e um que permite o acesso aos serviços padrão do Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Implemente <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> o método para instanciar o manipulador de comando.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Implementar o manipulador de comando de conclusão
 Como a conclusão da declaração é desencadeada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> por pressionamentos de teclas, você deve implementar a interface para receber e processar as teclas que disparam, comprometem e descartam a sessão de conclusão.

#### <a name="to-implement-the-completion-command-handler"></a>Para implementar o manipulador de comando de conclusão

1. Adicionar uma `TestCompletionCommandHandler` classe nomeada <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>que implementa:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Adicione campos privados para o próximo manipulador de comando (para o qual você passa o comando), a exibição de texto, o provedor de manipulador de comando (que permite o acesso a vários serviços) e uma sessão de conclusão:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Adicione um construtor que define a exibição de texto e os campos do provedor e adicione o comando à cadeia de comando:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> o método passando o comando adiante:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Implementar o método de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> . Quando este método recebe um toque de tecla, ele deve fazer uma dessas coisas:

   - Permitir que o caractere seja gravado no buffer e, em seguida, acionar ou filtrar a conclusão. (Imprimir caracteres faça isso.)

   - Comprometa a conclusão, mas não permita que o caractere seja escrito no buffer. (Whitespace, **Tab**e **Enter** façam isso quando uma sessão de conclusão for exibida.)

   - Permita que o comando seja passado para o próximo manipulador. (Todos os outros comandos.)

     Como esse método pode exibir <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> interface do i-u, ligue para ter certeza de que não é chamado em um contexto de automação:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Este código é um método privado que desencadeia a sessão de conclusão:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. O próximo exemplo é um método privado <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> que cancela a inscrição do evento:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Construa e teste o código
 Para testar este código, construa a solução CompletionTest e execute-a na instância experimental.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Para construir e testar a solução CompletionTest

1. Compile a solução.

2. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

3. Crie um arquivo de texto e digite algum texto que inclua a palavra "adicionar".

4. Ao digitar primeiro "a" e depois "d", uma lista que contém "adição" e "adaptação" deve aparecer. Observe que a adição está selecionada. Quando você digita outro "d", a lista deve conter apenas "adição", que agora está selecionada. Você pode cometer "adição" pressionando a **tecla Spacebar**, **Tab**ou **Enter,** ou descartar a lista digitando Esc ou qualquer outra chave.

## <a name="see-also"></a>Confira também
- [Passo a passo: Vincule um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
