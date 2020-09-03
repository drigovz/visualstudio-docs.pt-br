---
title: 'Walkthrough: implementando trechos de código | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb720589bc9bc31b7cf2a04b05559cb9c9d46961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201989"
---
# <a name="walkthrough-implementing-code-snippets"></a>Passo a passo: implementando snippets de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode criar trechos de código e incluí-los em uma extensão de editor para que os usuários da extensão possam adicioná-los ao seu próprio código.  
  
 Um trecho de código é um fragmento de código ou outro texto que pode ser incorporado em um arquivo. Para exibir todos os trechos de código que foram registrados para linguagens de programação específicas, no menu **ferramentas** , clique em **Code snippet Manager**. Para inserir um trecho em um arquivo, clique com o botão direito do mouse no local em que você deseja o trecho de código, clique em **Inserir trecho de código** ou **Circundar com**, localize o trecho desejado e clique duas vezes nele. Pressione TAB ou SHIFT + TAB para modificar as partes relevantes do trecho e pressione ENTER ou ESC para aceitá-las. Para obter mais informações, consulte [Snippets de Código](../ide/code-snippets.md).  
  
 Um trecho de código está contido em um arquivo XML que tem a extensão de nome de arquivo. snippet. Um trecho de código pode conter campos que são realçados depois que o trecho de código é inserido para que o usuário possa encontrá-los e alterá-los. Um arquivo de trecho também fornece informações para o **Gerenciador de trechos de código** para que ele possa exibir o nome do trecho na categoria correta. Para obter informações sobre o esquema de trecho, consulte [referência de esquema de trechos de código](../ide/code-snippets-schema-reference.md).  
  
 Este tutorial ensina como realizar essas tarefas:  
  
1. Criar e registrar trechos de código para um idioma específico.  
  
2. Adicione o comando **Inserir trecho** a um menu de atalho.  
  
3. Implemente a expansão do trecho.  
  
   Este guia passo a passo é baseado em [Walkthrough: exibindo a conclusão da instrução](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-and-registering-code-snippets"></a>Criando e registrando trechos de código  
 Normalmente, os trechos de código são associados a um serviço de idioma registrado. No entanto, você não precisa implementar um <xref:Microsoft.VisualStudio.Package.LanguageService> para registrar trechos de código. Em vez disso, basta especificar um GUID no arquivo de índice de trecho e, em seguida, usar o mesmo GUID no <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> que você adiciona ao seu projeto.  
  
 As etapas a seguir demonstram como criar trechos de código e associá-los a um GUID específico.  
  
1. Crie a seguinte estrutura de diretório:  
  
    **%InstallDir%\TestSnippets\Snippets\1033\\**  
  
    em que *% installdir%* é a pasta de instalação do Visual Studio. (Embora esse caminho seja normalmente usado para instalar trechos de código, você pode especificar qualquer caminho.)  
  
2. Na pasta \ 1033 \, crie um arquivo. xml e nomeie-o **TestSnippets.xml**. (Embora esse nome seja normalmente usado para um arquivo de índice de trecho de código, você pode especificar qualquer nome desde que ele tenha uma extensão de nome de arquivo. xml.) Adicione o texto a seguir e, em seguida, exclua o GUID do espaço reservado e adicione o seu próprio.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <SnippetCollection>  
       <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}">  
           <SnippetDir>  
               <OnOff>On</OnOff>  
               <Installed>true</Installed>  
               <Locale>1033</Locale>  
               <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath>  
               <LocalizedName>Snippets</LocalizedName>  
           </SnippetDir>  
       </Language>  
   </SnippetCollection>  
   ```  
  
3. Crie um arquivo na pasta trecho, nomeie-o como **Test** `.snippet` e, em seguida, adicione o seguinte texto:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
       <CodeSnippet Format="1.0.0">  
           <Header>  
               <Title>Test replacement fields</Title>  
               <Shortcut>test</Shortcut>  
               <Description>Code snippet for testing replacement fields</Description>  
               <Author>MSIT</Author>  
               <SnippetTypes>  
                   <SnippetType>Expansion</SnippetType>  
               </SnippetTypes>  
           </Header>  
           <Snippet>  
               <Declarations>  
                   <Literal>  
                     <ID>param1</ID>  
                       <ToolTip>First field</ToolTip>  
                       <Default>first</Default>  
                   </Literal>  
                   <Literal>  
                       <ID>param2</ID>  
                       <ToolTip>Second field</ToolTip>  
                       <Default>second</Default>  
                   </Literal>  
               </Declarations>  
               <References>  
                  <Reference>  
                      <Assembly>System.Windows.Forms.dll</Assembly>  
                  </Reference>  
               </References>  
               <Code Language="TestSnippets">  
                   <![CDATA[MessageBox.Show("$param1$");  
        MessageBox.Show("$param2$");]]>  
               </Code>    
           </Snippet>  
       </CodeSnippet>  
   </CodeSnippets>  
   ```  
  
   As etapas a seguir mostram como registrar os trechos de código.  
  
#### <a name="to-register-code-snippets-for-a-specific-guid"></a>Para registrar trechos de código para um GUID específico  
  
1. Abra o projeto **CompletionTest** . Para obter informações sobre como criar esse projeto, consulte [passo a passos: exibindo a conclusão da instrução](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2. No projeto, adicione referências aos seguintes assemblies:  
  
    - Microsoft. VisualStudio. Textmanager. Interop  
  
    - Microsoft. VisualStudio. Textmanager. Interop. 8.0  
  
    - Microsoft. MSXML  
  
3. No projeto, abra o arquivo Source. Extension. vsixmanifest.  
  
4. Verifique se a guia **ativos** contém um tipo de conteúdo **VSPackage** e se o **projeto** está definido como o nome do projeto.  
  
5. Selecione o projeto CompletionTest e, no janela Propriedades definir **gerar arquivo pkgdef** como **verdadeiro**. Salve o projeto.  
  
6. Adicione uma `SnippetUtilities` classe estática ao projeto.  
  
     [!code-csharp[VSSDKCompletionTest#22](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#22)]
     [!code-vb[VSSDKCompletionTest#22](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#22)]  
  
7. Na classe SnippetUtilities, defina um GUID e dê a ele o valor que você usou no arquivo de SnippetsIndex.xml.  
  
     [!code-csharp[VSSDKCompletionTest#23](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#23)]
     [!code-vb[VSSDKCompletionTest#23](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#23)]  
  
8. Adicione o <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> à `TestCompletionHandler` classe. Esse atributo pode ser adicionado a qualquer classe pública ou interna (não estática) no projeto. (Talvez você precise adicionar uma `using` instrução para o namespace Microsoft. VisualStudio. Shell.)  
  
     [!code-csharp[VSSDKCompletionTest#24](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#24)]
     [!code-vb[VSSDKCompletionTest#24](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#24)]  
  
9. Compile e execute o projeto. Na instância experimental do Visual Studio que começa quando o projeto é executado, o trecho que você acabou de registrar deve ser exibido no **Gerenciador de trechos de código** sob a linguagem **TestSnippets** .  
  
## <a name="adding-the-insert-snippet-command-to-the-shortcut-menu"></a>Adicionando o comando Inserir trecho ao menu de atalho  
 O comando **Inserir trecho de código** não está incluído no menu de atalho para um arquivo de texto. Portanto, você deve habilitar o comando.  
  
#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para adicionar o comando Inserir trecho ao menu de atalho  
  
1. Abra o `TestCompletionCommandHandler` arquivo de classe.  
  
     Como essa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , você pode ativar o comando **Insert Snippet** no <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método. Antes de habilitar o comando, verifique se esse método não está sendo chamado dentro de uma função de automação porque, quando o comando **Inserir trecho de código** for clicado, ele exibirá a interface do usuário do seletor de trecho de código.  
  
     [!code-csharp[VSSDKCompletionTest#25](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#25)]
     [!code-vb[VSSDKCompletionTest#25](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#25)]  
  
2. Compile e execute o projeto. Na instância experimental, abra um arquivo que tenha a extensão de nome de arquivo. zzz e clique com o botão direito do mouse em qualquer lugar. O comando **Inserir trecho de código** deve aparecer no menu de atalho.  
  
## <a name="implementing-snippet-expansion-in-the-snippet-picker-ui"></a>Implementando a expansão do trecho na interface do usuário do seletor de trecho  
 Esta seção mostra como implementar a expansão do trecho de código para que a interface do usuário do seletor de trecho seja exibida quando o **trecho de inserção** for clicado no menu de atalho. Um trecho de código também é expandido quando um usuário digita o atalho de trecho de código e pressiona TAB.  
  
 Para exibir a interface do usuário do seletor de trecho e habilitar a aceitação do trecho de navegação e de pós-inserção, use o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. A própria inserção é manipulada pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> método.  
  
 A implementação da expansão do trecho de código usa interfaces herdadas <xref:Microsoft.VisualStudio.TextManager.Interop> . Quando você traduz das classes de editor atuais para o código herdado, lembre-se de que as interfaces herdadas usam uma combinação de números de linha e números de coluna para especificar locais em um buffer de texto, mas as classes atuais usam um índice. Portanto, se um buffer tiver três linhas, cada uma delas terá dez caracteres (mais uma nova linha, que conta como um caractere), o quarto caractere na terceira ficará na posição 27 da implementação atual, mas está na linha 2, posição 3 na implementação antiga.  
  
#### <a name="to-implement-snippet-expansion"></a>Para implementar a expansão de trecho  
  
1. Para o arquivo que contém a `TestCompletionCommandHandler` classe, adicione as instruções a seguir `using` .  
  
     [!code-csharp[VSSDKCompletionTest#26](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#26)]
     [!code-vb[VSSDKCompletionTest#26](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#26)]  
  
2. Faça a `TestCompletionCommandHandler` classe implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface.  
  
     [!code-csharp[VSSDKCompletionTest#27](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#27)]
     [!code-vb[VSSDKCompletionTest#27](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#27)]  
  
3. Na `TestCompletionCommandHandlerProvider` classe, importe o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .  
  
     [!code-csharp[VSSDKCompletionTest#28](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#28)]
     [!code-vb[VSSDKCompletionTest#28](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#28)]  
  
4. Adicione alguns campos particulares para as interfaces de expansão de código e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#29](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#29)]
     [!code-vb[VSSDKCompletionTest#29](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#29)]  
  
5. No construtor da `TestCompletionCommandHandler` classe, defina os campos a seguir.  
  
     [!code-csharp[VSSDKCompletionTest#30](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#30)]
     [!code-vb[VSSDKCompletionTest#30](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#30)]  
  
6. Para exibir o seletor de trecho quando o usuário clica no comando **Insert Snippet** , adicione o seguinte código ao <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. (Para tornar essa explicação mais legível, o código exec () que é usado para conclusão de instrução não é mostrado; em vez disso, blocos de código são adicionados ao método existente.) Adicione o seguinte bloco de código após o código que verifica um caractere.  
  
     [!code-csharp[VSSDKCompletionTest#31](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#31)]
     [!code-vb[VSSDKCompletionTest#31](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#31)]  
  
7. Se um trecho de código tiver campos que possam ser navegados, a sessão de expansão será mantida aberta até que a expansão seja explicitamente aceita; Se o trecho de código não tiver campos, a sessão será fechada e retornada como `null` pelo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> método. No <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método, após o código da interface do usuário do seletor de trecho que você adicionou na etapa anterior, adicione o seguinte código para manipular a navegação do trecho (quando o usuário pressiona Tab ou SHIFT + TAB após a inserção do trecho de código).  
  
     [!code-csharp[VSSDKCompletionTest#32](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#32)]
     [!code-vb[VSSDKCompletionTest#32](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#32)]  
  
8. Para inserir o trecho de código quando o usuário digita o atalho correspondente e, em seguida, pressiona TAB, adicione o código ao <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método. O método particular que insere o trecho de código será mostrado em uma etapa posterior. Adicione o código a seguir após o código de navegação que você adicionou na etapa anterior.  
  
     [!code-csharp[VSSDKCompletionTest#33](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#33)]
     [!code-vb[VSSDKCompletionTest#33](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#33)]  
  
9. Implemente os métodos da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interface. Nessa implementação, os únicos métodos de interesse são <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . Os outros métodos devem apenas retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
     [!code-csharp[VSSDKCompletionTest#34](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#34)]
     [!code-vb[VSSDKCompletionTest#34](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#34)]  
  
10. Implementar o método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . O método auxiliar que realmente insere as expansões será abordado em uma etapa posterior. O <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> fornece informações de linha e coluna, que você pode obter do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
     [!code-csharp[VSSDKCompletionTest#35](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#35)]
     [!code-vb[VSSDKCompletionTest#35](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#35)]  
  
11. O método particular a seguir insere um trecho de código, com base no atalho ou no título e no caminho. Em seguida, ele chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> método com o trecho de código.  
  
     [!code-csharp[VSSDKCompletionTest#36](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/snippetutilities.cs#36)]
     [!code-vb[VSSDKCompletionTest#36](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/snippetutilities.vb#36)]  
  
## <a name="building-and-testing-code-snippet-expansion"></a>Criando e testando a expansão do trecho de código  
 Você pode testar se a expansão do trecho de código funciona em seu projeto.  
  
1. Compile a solução. Quando você executa esse projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
2. Abra um arquivo de texto e digite algum texto.  
  
3. Clique com o botão direito do mouse em algum lugar no texto e clique em **Inserir trecho**.  
  
4. A interface do usuário do seletor de trecho deve aparecer com um pop-up que diz **campos de substituição de teste**. Clique duas vezes no pop-up.  
  
     O trecho a seguir deve ser inserido.  
  
    ```  
    MessageBox.Show("first");  
    MessageBox.Show("second");  
    ```  
  
     Não pressione ENTER ou ESC.  
  
5. Pressione TAB e SHIFT + TAB para alternar entre "First" e "Second".  
  
6. Aceite a inserção pressionando ENTER ou ESC.  
  
7. Em uma parte diferente do texto, digite "Test" e pressione TAB. Como "Test" é o atalho de trecho de código, o trecho deve ser inserido novamente.  
  
## <a name="next-steps"></a>Próximas etapas
