---
title: 'Como: criar um aplicativo de serviço de fluxo de trabalho WCF | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605009"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Como: Crie um aplicativo de Serviço WCF de Fluxo de Trabalho
aplicativos de serviço do fluxo de trabalho[!INCLUDE[indigo1](../includes/indigo1-md.md)] são serviços de comunicação distribuídos que transmitem as mensagens entre clientes e eles próprios através dos limites de processo. A implementação do contrato de serviço no lado de serviço é feita declarativamente com as atividades de fluxo de trabalho em [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] de um modo semelhante aos serviços herdados de fluxo de trabalho no .NET Framework 3.5.

### <a name="to-create-a-wcf-workflow-service-application"></a>Para criar um aplicativo de serviço do fluxo de trabalho WCF

1. Inicie o [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. No menu **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...** .

     A caixa de diálogo **Novo Projeto** é aberta.

3. No painel **modelos instalados** , selecione **WCF** ou **fluxo de trabalho** de agrupamentos  **C# visuais** ou **Visual Basic** dependendo da linguagem de sua escolha.

4. No painel central, selecione **aplicativo de serviço de fluxo de trabalho WCF**.

5. Na caixa **nome** , insira um nome descritivo para o seu projeto para facilitar a identificação.

6. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7. Na caixa **solução** , selecione para criar uma nova solução e clique em **OK**.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console de fluxo de trabalho a uma solução existente, abra essa solução no [!INCLUDE[vs2010](../includes/vs2010-md.md)], clique com o botão direito do mouse na solução em **Gerenciador de soluções**e selecione **Adicionar**e **novo projeto...** para abrir a caixa de diálogo **novo projeto** . Continuar conforme descrito acima neste procedimento.

8. O modelo de projeto cria uma definição de serviço como XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] abre para o modo design com uma atividade de <xref:System.Activities.Statements.Sequence> que contém um conjunto de <xref:System.ServiceModel.Activities.Receive> e de atividades de <xref:System.ServiceModel.Activities.SendReply> .

## <a name="see-also"></a>Consulte também
 [Como criar uma atividade](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)