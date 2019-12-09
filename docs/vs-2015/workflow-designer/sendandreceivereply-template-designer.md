---
title: Designer de modelos SendAndReceiveReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4ecb0e201c4351a8a117d1e35aca97866b2beb89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663277"
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply
O modelo **SendAndReceiveReply** é usado para criar um par de atividades pré-configuradas de <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> em uma atividade <xref:System.Activities.Statements.Sequence> que estão correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no cliente.

## <a name="the-sendandreceivereply-template"></a>O modelo de SendAndReceiveReply
 A adição do modelo **SendAndReceiveReply** faz três coisas além da criação das atividades <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> dentro de uma atividade <xref:System.Activities.Statements.Sequence>:

1. Configurar <xref:System.ServiceModel.Activities.Send.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Send> .

2. Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .

3. Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="using-the-sendandreceivereply-template-designer"></a>Usando o designer do modelo de SendAndReceiveReply
 O designer de atividade **SendAndReceiveReply** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** em [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** na **exibição** menu ou CTRL + ALT + X.)

 O designer de atividade do **SendAndReceiveReply** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Send> que pode ser configurada com o designer de atividade de **envio** e uma <xref:System.ServiceModel.Activities.ReceiveReply> correlacionada que pode ser configurada com o designer de **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando o designer de **envio** para configurar a atividade de <xref:System.ServiceModel.Activities.Send>, consulte o tópico [Enviar](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando o designer **ReceiveReplyForSend** para configurar a atividade de <xref:System.ServiceModel.Activities.ReceiveReply>, consulte a seção a seguir.

### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.ReceiveReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer.

|                                 Nome da Propriedade                                 | Necessária |                                                                                                                                                                                                                                                                                                                                                        Uso                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  False   |                                                                                                                                                                                            O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   verdadeiro   | Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Send> e as atividades de <xref:System.ServiceModel.Activities.ReceiveReply> são usados juntos no cliente para modelar um padrão de mensagem de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  False   |                        Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de elipse ao lado do campo **conteúdo** na grade de propriedades ou clicando em **definir...** botão ao lado do rótulo de **conteúdo** na superfície do designer de atividade **Receive** . Ambos exibem a caixa de diálogo **definição de conteúdo** . [!INCLUDE[crabout](../includes/crabout-md.md)] como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  False   |              Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da propriedade <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> na grade Propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . [!INCLUDE[crabout](../includes/crabout-md.md)] usando essa caixa, consulte o tópico [Adicionar CorrelationInitializers da caixa de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  False   |                                                                                                                                                                                                                                               Especifica o cabeçalho da ação de mensagem. Se não é explicitamente definida, seu valor por padrão:<br /><br /> <strong>https://tempuri.org/{service o namespace de contrato}/{Service nome do contrato}/{Operation nome}.</strong>                                                                                                                                                                                                                                               |

## <a name="see-also"></a>Consulte também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [receber](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Enviar](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)