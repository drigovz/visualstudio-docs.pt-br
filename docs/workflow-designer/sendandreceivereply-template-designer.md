---
title: Designer de modelos Designer de Fluxo de Trabalho-SendAndReceiveReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7c552e8bb94ed9035f25bdd40b7944458e61a11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649964"
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply

O modelo **SendAndReceiveReply** é usado para criar um par de atividades pré-configuradas de <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply>. As atividades fazem parte de uma atividade de <xref:System.Activities.Statements.Sequence> e são correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no cliente.

## <a name="the-sendandreceivereply-template"></a>O modelo SendAndReceiveReply

Adicionar o modelo **SendAndReceiveReply** faz três coisas além da criação das atividades <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> dentro de uma atividade <xref:System.Activities.Statements.Sequence>:

- Configura as propriedades <xref:System.ServiceModel.Activities.Send.OperationName%2A> e <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> da atividade <xref:System.ServiceModel.Activities.Send>.

- Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .

- Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usar o designer de modelos SendAndReceiveReply

Acesse o designer de atividades do **SendAndReceiveReply** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade do **SendAndReceiveReply** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. O descarte do designer de atividade cria uma atividade de <xref:System.ServiceModel.Activities.Send> que pode ser configurada com o designer de atividade de **envio** e uma <xref:System.ServiceModel.Activities.ReceiveReply> correlacionada que pode ser configurada com o designer de **ReceiveReplyForSend** .

Para obter mais informações sobre como usar o designer de **envio** para configurar a atividade de <xref:System.ServiceModel.Activities.Send>, consulte [Enviar](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply

A tabela a seguir mostra as propriedades <xref:System.ServiceModel.Activities.ReceiveReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície de Designer de Fluxo de Trabalho.

| Nome da Propriedade | Necessária | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para o <xref:System.Activities.Activity.DisplayName%2A> amigável não seja estritamente necessário, é melhor usar esse valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | verdadeiro | Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Send> e as atividades de <xref:System.ServiceModel.Activities.ReceiveReply> são usados juntos no cliente para modelar um padrão de mensagem de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar essa propriedade porque ela é associada automaticamente à atividade de <xref:System.ServiceModel.Activities.Send> da qual você criou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply>. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | False | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de reticências ao lado do campo **conteúdo** na grade de propriedades ou clicando no botão **definir** ao lado do rótulo de **conteúdo** na superfície do designer de atividade **receber** . Ambos exibem a caixa de diálogo **definição de conteúdo** . Para obter mais informações sobre como usar essa caixa, consulte a [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | False | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da propriedade <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> na grade Propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . Para obter mais informações sobre como usar essa caixa, consulte [Adicionar CorrelationInitializers caixa de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | False | Especifica o cabeçalho da ação de mensagem. Se não estiver definido explicitamente, seu valor padrão será:<br /><br /> <strong>https://tempuri.org/{service o namespace de contrato}/{Service nome do contrato}/{Operation nome}.</strong> |

## <a name="see-also"></a>Consulte também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)