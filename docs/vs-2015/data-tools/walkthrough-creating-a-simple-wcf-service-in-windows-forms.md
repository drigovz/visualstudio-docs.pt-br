---
title: 'Walkthrough: Criando um serviço WCF simples no Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 366567a13ad23ab19ffd88f19997b92025abe952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671072"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Passo a passo: criando um Serviço WCF simples no Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial demonstra como criar um serviço simples [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] , testá-lo e, em seguida, acessá-lo de um aplicativo Windows Forms.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Criando o serviço

#### <a name="to-create-a-wcf-service"></a>Para criar um serviço WCF

1. No menu **arquivo** , aponte para **novo** e clique em **projeto**.

2. Na caixa de diálogo **novo projeto** , expanda o nó **Visual Basic** ou **Visual C#** e clique em **WCF**, seguido pela **biblioteca de serviços WCF**. Clique em **OK** para abrir o projeto.

     ![O projeto da biblioteca de serviços do WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Isso cria um serviço de trabalho que pode ser testado e acessado. As duas etapas a seguir demonstram como você pode modificar o método padrão para usar um tipo de dados diferente. Em um aplicativo real, você também adicionaria suas próprias funções ao serviço.

3. ![O arquivo IService1](../data-tools/media/wcf2.png "wcf2")

     Em **Gerenciador de soluções**, clique duas vezes em IService1. vb ou IService1.cs e localize a seguinte linha:

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Altere o tipo para o `value` parâmetro para `String` :

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     No código acima, observe os `<OperationContract()>` atributos ou `[OperationContract]` . Esses atributos são necessários para qualquer método exposto pelo serviço.

4. ![O arquivo Service1](../data-tools/media/wcf3.png "wcf3")

     Em **Gerenciador de soluções**, clique duas vezes em Service1. vb ou Service1.cs e localize a seguinte linha:

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Altere o tipo para o parâmetro de valor para `String` :

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Testando o serviço

#### <a name="to-test-a-wcf-service"></a>Para testar um serviço WCF

1. Pressione **F5** para executar o serviço. Um formulário de **cliente de teste do WCF** será exibido e o serviço será carregado.

2. No formulário do **cliente de teste do WCF** , clique duas vezes no método **GetData ()** em **IService1**. A guia **GetData** será exibida.

     ![O método GetData&#40;&#41; ](../data-tools/media/wcf4.png "wcf4")

3. Na caixa **solicitação** , selecione o campo **valor** e digite `Hello` .

     ![O campo de valor](../data-tools/media/wcf5.png "wcf5")

4. Clique no botão **invocar** . Se uma caixa de diálogo **aviso de segurança** for exibida, clique em **OK**. O resultado será exibido na caixa **resposta** .

     ![O resultado na caixa de resposta](../data-tools/media/wcf6.png "wcf6")

5. No menu **arquivo** , clique em **sair** para fechar o formulário de teste.

## <a name="accessing-the-service"></a>Acessando o serviço

#### <a name="to-reference-a-wcf-service"></a>Para fazer referência a um serviço WCF

1. No menu **arquivo** , aponte para **Adicionar** e clique em **novo projeto**.

2. Na caixa de diálogo **novo projeto** , expanda o nó **Visual Basic** ou **Visual C#** e selecione **Windows**e, em seguida, selecione **Windows Forms aplicativo**. Clique em **OK** para abrir o projeto.

     ![Windows Forms projeto de aplicativo](../data-tools/media/wcf7.png "wcf7")

3. Clique com o botão direito do mouse em **WindowsApplication1** e clique em **Adicionar referência de serviço**. A caixa de diálogo **Adicionar referência de serviço** será exibida.

4. Na caixa de diálogo **Adicionar Referência de Serviço**, clique em **Descobrir**.

     ![A caixa de diálogo Adicionar Referência de Serviço](../data-tools/media/wcf8.png "wcf8")

     **Service1** será exibido no painel **Serviços** .

5. Clique em **OK** para adicionar a referência de serviço.

#### <a name="to-build-a-client-application"></a>Para criar um aplicativo cliente

1. Em **Gerenciador de soluções**, clique duas vezes em **Form1. vb** ou **Form1.cs** para abrir a designer de formulários do Windows se ela ainda não estiver aberta.

2. Na **caixa de ferramentas**, arraste um `TextBox` controle, `Label` um controle e um `Button` controle para o formulário.

     ![Adicionando controles ao formulário](../data-tools/media/wcf9.png "wcf9")

3. Clique duas vezes em `Button` e adicione o seguinte código ao manipulador de `Click` eventos:

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. Em **Gerenciador de soluções**, clique com o botão direito do mouse em **WindowsApplication1** e clique em **definir como projeto de inicialização**.

5. Pressione **F5** para executar o projeto. Insira algum texto e clique no botão. O rótulo exibirá "você inseriu:" e o texto que você inseriu.

     ![O formulário que mostra o resultado](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Consulte Também
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
