---
title: Designer de modelos Designer de Fluxo de Trabalho-ReceiveAndSendReply
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a816013f4eceb390a16e76a06814043aa0adaeb8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650028"
---
# <a name="receiveandsendreply-template-designer"></a>Designer do modelo de ReceiveAndSendReply

O modelo **ReceiveAndSendReply** é usado para criar um par de atividades pré-configuradas de <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>. As atividades fazem parte de uma atividade de <xref:System.Activities.Statements.Sequence> e são correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no servidor.

## <a name="the-receiveandsendreply-template"></a>O modelo ReceiveAndSendReply

Adicionar um modelo **ReceiveAndSendReply** faz três coisas além da criação das atividades <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> com uma atividade <xref:System.Activities.Statements.Sequence>:

- Configura as propriedades <xref:System.ServiceModel.Activities.Receive.OperationName%2A> e <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> da atividade <xref:System.ServiceModel.Activities.Receive>.

- Associa a propriedade de <xref:System.ServiceModel.Activities.SendReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> a atividade de <xref:System.ServiceModel.Activities.Send> .

- Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usar o designer de modelos ReceiveAndSendReply

Acesse o designer de atividades do **ReceiveAndSendReply** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade do **ReceiveAndSendReply** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. O descarte do designer de atividade cria uma atividade de <xref:System.ServiceModel.Activities.Receive> que pode ser configurada com o designer de atividade de **envio** e uma <xref:System.ServiceModel.Activities.SendReply> correlacionada que pode ser configurada com o designer de SendReplyToReceive.

Para obter mais informações sobre como usar o designer de **recebimento** para configurar a atividade de <xref:System.ServiceModel.Activities.Receive>, consulte [receber designer de atividade](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propriedades de SendReply

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.SendReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície de Designer de Fluxo de Trabalho.

| Nome da Propriedade | Necessária | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.SendReply> . O padrão é SendReplyToReceive.<br /><br /> Embora o uso de um valor não padrão para o <xref:System.Activities.Activity.DisplayName%2A> amigável não seja estritamente necessário, é melhor usar esse valor. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | verdadeiro | Fazer referência a <xref:System.ServiceModel.Activities.Receive> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.SendReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Receive> e as atividades de <xref:System.ServiceModel.Activities.SendReply> são usados juntos no servidor para modelar um padrão de mensagem de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar essa propriedade porque ela é associada automaticamente à atividade de <xref:System.ServiceModel.Activities.Send> da qual você criou a atividade de <xref:System.ServiceModel.Activities.SendReply>. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | False | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de reticências ao lado do campo **conteúdo** na grade de propriedades ou clicando no botão **definir** ao lado do rótulo **conteúdo** na superfície **receber** designer de atividade. Ambos exibem a caixa de diálogo **definição de conteúdo** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | False | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da propriedade <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> na grade Propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | False | Especifica o cabeçalho da ação de mensagem. Se não estiver definido explicitamente, seu valor padrão será:<br /><br /> <strong>https://tempuri.org/{service o namespace do contrato} nome do contrato/{Service}/{Operation nome}</strong> |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | False | Especifica se a instância de fluxo de trabalho deve ser persistentes antes que a mensagem de resposta que é enviada. O valor padrão é **false**. |

## <a name="see-also"></a>Consulte também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)