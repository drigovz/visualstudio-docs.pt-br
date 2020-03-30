---
title: Designer de fluxo de trabalho - SendAndReceiveReply Model Designer
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
ms.openlocfilehash: 2067ee92883d0c4ad3003f23032a88f5da3fa710
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395241"
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply

O modelo **SendAndReceiveReply** é usado para criar <xref:System.ServiceModel.Activities.Send> um <xref:System.ServiceModel.Activities.ReceiveReply> par de atividades pré-configuradas. As atividades fazem <xref:System.Activities.Statements.Sequence> parte de uma atividade e estão correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no cliente.

## <a name="the-sendandreceivereply-template"></a>O modelo EnviareReceberResposta

Adicionar o modelo **SendAndReceiveReply** faz <xref:System.ServiceModel.Activities.Send> três <xref:System.ServiceModel.Activities.ReceiveReply> coisas <xref:System.Activities.Statements.Sequence> além de criar as atividades dentro de uma atividade:

- Configura as <xref:System.ServiceModel.Activities.Send.OperationName%2A> <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> propriedades da <xref:System.ServiceModel.Activities.Send> atividade.

- Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .

- Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="use-the-sendandreceivereply-template-designer"></a>Use o designer de modelosendandreceivereply

Acesse o designer de atividades **SendAndReceiveReply** na categoria **Mensagens** da Caixa de **Ferramentas**. O designer de atividades **SendAndReceiveReply** pode ser arrastado da caixa de **ferramentas** e jogado na superfície do Workflow Designer onde as atividades geralmente são colocadas. A queda do <xref:System.ServiceModel.Activities.Send> designer de atividades cria uma atividade que <xref:System.ServiceModel.Activities.ReceiveReply> pode ser configurada com o designer de atividades **Send** e uma correlacionada que pode ser configurada com o designer **ReceiveReplyForSend.**

Para obter mais informações sobre como <xref:System.ServiceModel.Activities.Send> usar o designer **Enviar** para configurar a atividade, consulte [Enviar](../workflow-designer/send-activity-designer.md).

### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply

A tabela a <xref:System.ServiceModel.Activities.ReceiveReply> seguir mostra as propriedades e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades, e algumas podem ser editadas na superfície workflow designer.

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor <xref:System.Activities.Activity.DisplayName%2A> não padrão para o amigável não seja estritamente necessário, é melhor usar esse valor. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> | True | Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Esta propriedade não deve ser **nula.** <xref:System.ServiceModel.Activities.Send>e <xref:System.ServiceModel.Activities.ReceiveReply> as atividades são usadas em conjunto no cliente para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade porque ela <xref:System.ServiceModel.Activities.Send> está automaticamente ligada <xref:System.ServiceModel.Activities.ReceiveReply> à atividade a partir da qual você criou a atividade. |
| <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite esta propriedade clicando no botão ellipsis ao lado do campo **Conteúdo** na grade da propriedade ou clicando no botão **Definir** ao lado da etiqueta **Conteúdo** na superfície do designer de **atividades Receber.** Ambos exibem a caixa de diálogo Definição de **conteúdo.** Para obter mais informações sobre como usar esta caixa, consulte [Caixa de diálogo de definição de conteúdo](../workflow-designer/content-definition-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão elipse <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> ao lado da propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar iniciadores de correlação.** Para obter mais informações sobre o uso desta caixa, consulte [Adicionar caixa de diálogo CorrelaçõesInicializantes](../workflow-designer/add-correlationinitializers-dialog-box.md). |
| <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se não for explicitamente definido, seu valor será padrão para:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Confira também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)