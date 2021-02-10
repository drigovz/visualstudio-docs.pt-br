---
title: Designer do modelo de SendAndReceiveReply
description: Saiba como você pode usar o modelo SendAndReceiveReply em Designer de Fluxo de Trabalho para criar um par de atividades de envio e ReceiveReply pré-configuradas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02bcc4a812a541ea792a190dc21dfbeb3119c008
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943686"
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply

O modelo **SendAndReceiveReply** é usado para criar um par de atividades pré-configuradas e predefinidas <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . As atividades fazem parte de uma <xref:System.Activities.Statements.Sequence> atividade e são correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no cliente.

## <a name="the-sendandreceivereply-template"></a>O modelo SendAndReceiveReply

Adicionar o modelo **SendAndReceiveReply** faz três coisas além da criação <xref:System.ServiceModel.Activities.Send> das <xref:System.ServiceModel.Activities.ReceiveReply> atividades e dentro de uma <xref:System.Activities.Statements.Sequence> atividade:

- Configura as <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> Propriedades e da <xref:System.ServiceModel.Activities.Send> atividade.

- Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .

- Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="use-the-sendandreceivereply-template-designer"></a>Usar o designer de modelos SendAndReceiveReply

Acesse o designer de atividades do **SendAndReceiveReply** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade do **SendAndReceiveReply** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. Descartar o designer de atividade cria uma <xref:System.ServiceModel.Activities.Send> atividade que pode ser configurada com o designer de atividade de **envio** e uma correlacionada <xref:System.ServiceModel.Activities.ReceiveReply> que pode ser configurada com o designer de **ReceiveReplyForSend** .

Para obter mais informações sobre como usar o designer de **envio** para configurar a <xref:System.ServiceModel.Activities.Send> atividade, consulte [Enviar](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply

A tabela a seguir mostra as <xref:System.ServiceModel.Activities.ReceiveReply> Propriedades e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície de Designer de Fluxo de Trabalho.

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para o amigável <xref:System.Activities.Activity.DisplayName%2A> não seja estritamente necessário, é melhor usar esse valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> as atividades são usadas em conjunto no cliente para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar essa propriedade porque ela é associada automaticamente à <xref:System.ServiceModel.Activities.Send> atividade da qual você criou a <xref:System.ServiceModel.Activities.ReceiveReply> atividade. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de reticências ao lado do campo **conteúdo** na grade de propriedades ou clicando no botão **definir** ao lado do rótulo de **conteúdo** na superfície do designer de atividade **receber** . Ambos exibem a caixa de diálogo **definição de conteúdo** . Para obter mais informações sobre como usar essa caixa, consulte a [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . Para obter mais informações sobre como usar essa caixa, consulte [Adicionar CorrelationInitializers caixa de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se não estiver definido explicitamente, seu valor padrão será:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Confira também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recebe](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)