---
title: 'Passo a passo: Implementando trechos de código | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: ba1b6e0852c1ec1b306938b791eed78e79d211ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697093"
---
# <a name="walkthrough-implement-code-snippets"></a>Passo a passo: Implementar trechos de código
Você pode criar trechos de código e incluí-los em uma extensão de editor para que os usuários da extensão possam adicioná-los ao seu próprio código.

 Um trecho de código é um fragmento de código ou outro texto que pode ser incorporado em um arquivo. Para visualizar todos os trechos registrados para linguagens de programação específicas, no menu **Ferramentas,** clique em **Code Snippet Manager**. Para inserir um trecho em um arquivo, clique com o botão direito do mouse onde deseja o trecho, clique em Inserir trecho ou **'Rode' com**, localize o trecho que deseja e clique duas vezes nele. Pressione **Guia** ou Guia **de**+**Deslocamento** para modificar as partes relevantes do trecho e, em seguida, **pressione Enter** ou **Esc** para aceitá-lo. Para obter mais informações, consulte [trechos de código](../ide/code-snippets.md).

 Um trecho de código está contido em um arquivo XML que tem a extensão de nome do arquivo .snippet*. Um trecho pode conter campos que são destacados após a inserção do trecho para que o usuário possa encontrá-los e alterá-los. Um arquivo de trecho também fornece informações para o **Gerenciador de trechos de código** para que ele possa exibir o nome do trecho na categoria correta. Para obter informações sobre o esquema de trechos, consulte [A referência do esquema de trechos de código](../ide/code-snippets-schema-reference.md).

 Este passo a passo ensina como realizar essas tarefas:

1. Crie e registre trechos de código para um idioma específico.

2. Adicione o comando **Inserir snippet** a um menu de atalho.

3. Implementar expansão de trechos.

   Este passo a passo é baseado no [passo a passo: conclusão da declaração de exibição](../extensibility/walkthrough-displaying-statement-completion.md).

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-and-register-code-snippets"></a>Criar e registrar trechos de código
 Normalmente, trechos de código são associados a um serviço de idioma registrado. No entanto, você não <xref:Microsoft.VisualStudio.Package.LanguageService> precisa implementar um para registrar trechos de código. Em vez disso, basta especificar um GUID no arquivo de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> índice de trecho e, em seguida, usar o mesmo GUID no que você adiciona ao seu projeto.

 As etapas a seguir demonstram como criar trechos de código e associá-los a um GUID específico.

1. Crie a seguinte estrutura de diretório:

    **%InstallDir%\TestSnippets\Snippets\1033\\**

    onde *%InstallDir%* é a pasta de instalação do Visual Studio. (Embora este caminho seja normalmente usado para instalar trechos de código, você pode especificar qualquer caminho.)

2. Na pasta \1033\, crie um arquivo *.xml* e nomeie-o **TestSnippets.xml**. (Embora este nome seja normalmente usado para um arquivo de índice de trecho, você pode especificar qualquer nome, desde que tenha uma extensão de nome de arquivo *.xml.)* Adicione o texto a seguir e, em seguida, exclua o GUID do espaço reservado e adicione o seu próprio.

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

3. Crie um arquivo na pasta de trechos, nomeie-o **como teste**`.snippet`e adicione o seguinte texto:

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

### <a name="to-register-code-snippets-for-a-specific-guid"></a>Para registrar trechos de código para um GUID específico

1. Abra o projeto **CompletionTest.** Para obter informações sobre como criar este projeto, consulte [Passo a Passo: Concluir a declaração de exibição](../extensibility/walkthrough-displaying-statement-completion.md).

2. No projeto, adicione referências às seguintes assembléias:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.TextManager.Interop.8.0

    - microsoft.msxml

3. No projeto, abra o arquivo **source.extension.vsixmanifest.**

4. Certifique-se **de** que a guia Ativos contenha um tipo de conteúdo **VsPackage** e que **o Projeto** esteja definido como o nome do projeto.

5. Selecione o projeto CompletionTest e no conjunto de janelas **Propriedades Gerar arquivo Pkgdef** para **true**. Salve o projeto.

6. Adicione uma `SnippetUtilities` classe estática ao projeto.

     [!code-csharp[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]

7. Na classe SnippetUtilities, defina um GUID e dê-lhe o valor que você usou no arquivo *SnippetsIndex.xml.*

     [!code-csharp[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]

8. Adicione <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> o `TestCompletionHandler` à classe. Esse atributo pode ser adicionado a qualquer classe pública ou interna (não estática) do projeto. (Você pode ter `using` que adicionar uma diretiva para o espaço de nome Microsoft.VisualStudio.Shell.)

     [!code-csharp[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]

9. Compile e execute o projeto. Na instância experimental do Visual Studio que começa quando o projeto é executado, o trecho que você acabou de registrar deve ser exibido no **Code Snippets Manager** sob a linguagem **TestSnippets.**

## <a name="add-the-insert-snippet-command-to-the-shortcut-menu"></a>Adicione o comando Inserir snippet ao menu de atalho
 O **comando Inserir snippet** não está incluído no menu de atalho para um arquivo de texto. Portanto, você deve ativar o comando.

#### <a name="to-add-the-insert-snippet-command-to-the-shortcut-menu"></a>Para adicionar o comando Inserir snippet ao menu de atalho

1. Abra `TestCompletionCommandHandler` o arquivo da classe.

     Como esta classe <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>implementa, você pode ativar o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> comando **Inserir snippet** no método. Antes de ativar o comando, verifique se esse método não está sendo chamado dentro de uma função de automação porque quando o comando **Insert Snippet** é clicado, ele exibe a interface do usuário do snippet picker (UI).

     [!code-csharp[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]

2. Compile e execute o projeto. Na instância experimental, abra um arquivo que tenha a extensão do nome do arquivo *.zzz* e clique com o botão direito do mouse em qualquer lugar nele. O **comando Inserir snippet** deve aparecer no menu de atalho.

## <a name="implement-snippet-expansion-in-the-snippet-picker-ui"></a>Implementar expansão de trechos na UI snippet Picker
 Esta seção mostra como implementar a expansão do trecho de código para que a iM do snippet picker seja exibida quando **Insert Snippet** é clicado no menu de atalho. Um trecho de código também é expandido quando um usuário digita o atalho de trecho de código e, em seguida, **pressiona Guia**.

 Para exibir a ui do snippet picker e para permitir a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> navegação e a aceitação pós-inserção de trechos, use o método. A inserção em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> si é tratada pelo método.

 A implementação da expansão <xref:Microsoft.VisualStudio.TextManager.Interop> do snippet de código usa interfaces legadas. Quando você traduzir das classes atuais do editor para o código legado, lembre-se de que as interfaces legados usam uma combinação de números de linha e números de coluna para especificar locais em um buffer de texto, mas as classes atuais usam um índice. Portanto, se um buffer tem três linhas cada uma com 10 caracteres (mais uma newline, que conta como um caractere), o quarto caractere na terceira linha está na posição 27 na implementação atual, mas está na linha 2, posição 3 na antiga implementação.

#### <a name="to-implement-snippet-expansion"></a>Para implementar a expansão do trecho

1. Ao arquivo que `TestCompletionCommandHandler` contém a classe, adicione as seguintes `using` diretivas.

     [!code-csharp[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]

2. Faça `TestCompletionCommandHandler` a classe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> implementar a interface.

     [!code-csharp[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]

3. Na `TestCompletionCommandHandlerProvider` classe, importe o <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.

     [!code-csharp[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]

4. Adicione alguns campos privados para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>as interfaces de expansão de código e o .

     [!code-csharp[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]

5. Na construtora da `TestCompletionCommandHandler` classe, defina os seguintes campos.

     [!code-csharp[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]

6. Para exibir o snippet picker quando o usuário clicar no comando Inserir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> **trecho,** adicione o seguinte código ao método. (Para tornar essa explicação mais `Exec()`legível, o código usado para conclusão da declaração não é mostrado; em vez disso, blocos de código são adicionados ao método existente.) Adicione o seguinte bloco de código após o código que verifica um caractere.

     [!code-csharp[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]

7. Se um trecho tiver campos que possam ser navegados, a sessão de expansão será mantida aberta até que a expansão seja explicitamente aceita; se o trecho não tiver campos, a sessão é `null` encerrada <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> e é devolvida pelo método. No <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método, após o código de ilicitu de snippet picker que você adicionou na etapa anterior, adicione o código a seguir para lidar com a navegação de trechos (quando o usuário pressionar **Tab** ou **Shift**+**Tab** após a inserção do trecho).

     [!code-csharp[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]

8. Para inserir o trecho de código quando o usuário digita o atalho <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> correspondente e, em seguida, **pressiona Guia,** adicione código ao método. O método privado que insere o trecho será mostrado em uma etapa posterior. Adicione o seguinte código após o código de navegação que você adicionou na etapa anterior.

     [!code-csharp[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]

9. Implementar os métodos <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> da interface. Nesta implementação, os únicos métodos de interesse são <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Os outros métodos <xref:Microsoft.VisualStudio.VSConstants.S_OK>devem apenas retornar.

     [!code-csharp[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]

10. Implementar o método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> . O método auxiliar que realmente insere as expansões é coberto em uma etapa posterior. As <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> informações de linha e coluna fornecem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>informações de linha e coluna, que você pode obter a partir do .

     [!code-csharp[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]

11. O método privado a seguir insere um trecho de código, baseado no atalho ou no título e no caminho. Em seguida, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> ele chama o método com o trecho.

     [!code-csharp[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]

## <a name="build-and-test-code-snippet-expansion"></a>Construir e testar a expansão do snippet do código
 Você pode testar se a expansão de trechos funciona em seu projeto.

1. Compile a solução. Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é iniciada.

2. Abra um arquivo de texto e digite algum texto.

3. Clique com o botão direito do mouse em algum lugar do texto e clique em **Inserir trecho**.

4. A ui do snippet deve aparecer com um pop-up que diz campos de **substituição de teste**. Clique duas vezes no pop-up.

     O seguinte trecho deve ser inserido.

    ```
    MessageBox.Show("first");
    MessageBox.Show("second");
    ```

     Não **pressione Enter** ou **Esc**.

5. Pressione **Tab** e **Shift**+**Tab** para alternar entre "primeiro" e "segundo".

6. Aceite a inserção pressionando **Enter** ou **Esc**.

7. Em uma parte diferente do texto, digite "teste" e, em seguida, **pressione Guia**. Como "teste" é o atalho de código-trecho, o trecho deve ser inserido novamente.

## <a name="next-steps"></a>Próximas etapas
