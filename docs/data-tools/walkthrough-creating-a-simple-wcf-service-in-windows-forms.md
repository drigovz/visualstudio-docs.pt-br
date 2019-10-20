---
title: 'Passo a passo: criando um Serviço WCF simples no Windows Forms'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7e2954d333ae3fe0dc6ff1c221d1e450eb9bf51a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639468"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Walkthrough: criar um serviço WCF simples no Windows Forms

Este tutorial demonstra como criar um serviço de Windows Communication Foundation simples (WCF), testá-lo e, em seguida, acessá-lo em um aplicativo Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Criar um serviço

1. Abra o Visual Studio.

::: moniker range="vs-2017"

2. No menu **Arquivo**, escolha **Novo** > **Projeto**.

3. Na caixa de diálogo **novo projeto** , expanda o **Visual Basic** ou o nó **Visual C#**  e escolha **WCF**, seguido pela **biblioteca de serviços WCF**.

4. Clique em **OK** para criar o projeto.

   ![O projeto da biblioteca de serviços do WCF](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Na tela Iniciar, selecione **Criar um novo projeto**.

3. Digite **biblioteca de serviços WCF** na caixa de pesquisa na página **criar um novo projeto** . Selecione o modelo C# ou Visual Basic para a **biblioteca de serviços do WCF**e clique em **Avançar**.

   ![Criar novo projeto de biblioteca de serviço WCF no Visual Studio 2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Se você não vir nenhum modelo, talvez seja necessário instalar o componente **Windows Communication Foundation** do Visual Studio. Escolha **instalar mais ferramentas e recursos** para abrir o instalador do Visual Studio. Escolha a guia **componentes individuais** , role para baixo até **atividades de desenvolvimento**e, em seguida, selecione **Windows Communication Foundation**. Clique em **Modificar**.

4. Na página **configurar seu novo projeto** , clique em **criar**.

::: moniker-end

   > [!NOTE]
   > Isso cria um serviço de trabalho que pode ser testado e acessado. As duas etapas a seguir demonstram como você pode modificar o método padrão para usar um tipo de dados diferente. Em um aplicativo real, você também adicionaria suas próprias funções ao serviço.

5. Em **Gerenciador de soluções**, clique duas vezes em **IService1. vb** ou **IService1.cs**.

   ![O arquivo IService1](../data-tools/media/wcf2.png)

   Localize a seguinte linha:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Altere o tipo do parâmetro `value` para cadeia de caracteres:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   No código acima, observe os atributos `<OperationContract()>` ou `[OperationContract]`. Esses atributos são necessários para qualquer método exposto pelo serviço.

6. Em **Gerenciador de soluções**, clique duas vezes em **Service1. vb** ou **Service1.cs**.

   ![O arquivo Service1](../data-tools/media/wcf3.png)

   Localize a seguinte linha:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Altere o tipo do parâmetro `value` para cadeia de caracteres:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testar o serviço

1. Pressione **F5** para executar o serviço. Um formulário de **cliente de teste do WCF** é exibido e carrega o serviço.

2. No formulário do **cliente de teste do WCF** , clique duas vezes no método **GetData ()** em **IService1**. A guia **GetData** é exibida.

     ![O método&#40; &#41; GetData](../data-tools/media/wcf4.png)

3. Na caixa **solicitação** , selecione o campo **valor** e digite `Hello`.

     ![O campo de valor](../data-tools/media/wcf5.png)

4. Clique no botão **invocar** . Se uma caixa de diálogo **aviso de segurança** for exibida, clique em **OK**. O resultado é exibido na caixa **resposta** .

     ![O resultado na caixa de resposta](../data-tools/media/wcf6.png)

5. No menu **arquivo** , clique em **sair** para fechar o formulário de teste.

## <a name="access-the-service"></a>Acessar o serviço

### <a name="reference-the-wcf-service"></a>Referenciar o serviço WCF

1. No menu **Arquivo**, aponte para **Adicionar** e clique em **Novo Projeto**.

2. Na caixa de diálogo **novo projeto** , expanda o **Visual Basic** ou o nó do **Visual C#**  , selecione **Windows**e, em seguida, selecione **Windows Forms aplicativo**. Clique em **OK** para abrir o projeto.

     ![Windows Forms projeto de aplicativo](../data-tools/media/wcf7.png)

3. Clique com o botão direito do mouse em **WindowsApplication1** e clique em **Adicionar referência de serviço**. A caixa de diálogo **Adicionar referência de serviço** é exibida.

4. Na caixa de diálogo **Adicionar Referência de Serviço**, clique em **Descobrir**.

     ![A caixa de diálogo Adicionar Referência de Serviço](../data-tools/media/wcf8.png)

     **Service1** é exibido no painel **Serviços** .

5. Clique em **OK** para adicionar a referência de serviço.

### <a name="build-a-client-application"></a>Criar um aplicativo cliente

1. Em **Gerenciador de soluções**, clique duas vezes em **Form1. vb** ou **Form1.cs** para abrir a designer de formulários do Windows se ela ainda não estiver aberta.

2. Na **caixa de ferramentas**, arraste um controle de `TextBox`, um controle de `Label` e um controle de `Button` para o formulário.

     ![Adicionando controles ao formulário](../data-tools/media/wcf9.png)

3. Clique duas vezes no `Button` e adicione o seguinte código no manipulador de eventos `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **WindowsApplication1** e clique em **definir como projeto de inicialização**.

5. Pressione **F5** para executar o projeto. Insira algum texto e clique no botão. O rótulo exibe "você inseriu:" e mostra o texto que você inseriu.

     ![O formulário que mostra o resultado](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Consulte também

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)