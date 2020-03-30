---
title: Designer de fluxo de trabalho - ReceiveAndSendReply Model Designer
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
ms.openlocfilehash: 042032efe745a9cb38bbf4e362cb5ad8440129ba
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395293"
---
# <a name="receiveandsendreply-template-designer"></a>Designer do modelo de ReceiveAndSendReply

O modelo **ReceiveAndSendReply** é usado para criar <xref:System.ServiceModel.Activities.Receive> um <xref:System.ServiceModel.Activities.SendReply> par de atividades pré-configuradas. As atividades fazem <xref:System.Activities.Statements.Sequence> parte de uma atividade e estão correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no servidor.

## <a name="the-receiveandsendreply-template"></a>O modelo ReceiveAndSendReply

Adicionar um modelo **ReceiveAndSendReply** faz <xref:System.ServiceModel.Activities.Receive> três <xref:System.ServiceModel.Activities.SendReply> coisas <xref:System.Activities.Statements.Sequence> além de criar as atividades e atividades com uma atividade:

- Configura as <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> propriedades da <xref:System.ServiceModel.Activities.Receive> atividade.

- Associa a propriedade de <xref:System.ServiceModel.Activities.SendReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> a atividade de <xref:System.ServiceModel.Activities.Send> .

- Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="use-the-receiveandsendreply-template-designer"></a>Use o designer de modeloreceiveandsendreply

Acesse o designer de atividades **ReceiveAndSendReply** na categoria **Mensagens** da Caixa de **Ferramentas**. O designer de atividades **ReceiveAndSendReply** pode ser arrastado da caixa de **ferramentas** e jogado na superfície do Workflow Designer onde as atividades geralmente são colocadas. A queda do <xref:System.ServiceModel.Activities.Receive> designer de atividades cria uma atividade que <xref:System.ServiceModel.Activities.SendReply> pode ser configurada com o designer de atividades **Send** e uma correlacionada que pode ser configurada com o designer SendReplyToReceive.

Para obter mais informações sobre como <xref:System.ServiceModel.Activities.Receive> usar o designer **Receber** para configurar a atividade, consulte Receber de Designer de [Atividades](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propriedades de SendReply

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.SendReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades, e algumas podem ser editadas na superfície workflow designer.

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.SendReply> . O padrão é SendReplyToReceive.<br /><br /> Embora o uso de um valor <xref:System.Activities.Activity.DisplayName%2A> não padrão para o amigável não seja estritamente necessário, é melhor usar esse valor. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Fazer referência a <xref:System.ServiceModel.Activities.Receive> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.SendReply> . Esta propriedade não deve ser **nula.** <xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.SendReply> as atividades são usadas em conjunto no servidor para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade porque ela <xref:System.ServiceModel.Activities.Send> está automaticamente ligada <xref:System.ServiceModel.Activities.SendReply> à atividade a partir da qual você criou a atividade. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite esta propriedade clicando no botão ellipsis ao lado do campo **Conteúdo** na grade de propriedade ou clicando no botão **Definir** ao lado da etiqueta **Conteúdo** na superfície do designer de **atividades Receber.** Ambos exibem a caixa de diálogo Definição de **conteúdo.** Para obter mais informações sobre como usar esta caixa, consulte o tópico [Caixa de Diálogo de Definição de Conteúdo.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão elipse <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> ao lado da propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar iniciadores de correlação.** Para obter mais informações sobre o uso desta caixa, consulte o tópico [Caixa de diálogo Adicionar correlaçãoInicializador.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se não for explicitamente definido, seu valor será padrão para:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Falso | Especifica se a instância de fluxo de trabalho deve ser persistentes antes que a mensagem de resposta que é enviada. O valor padrão é **false**. |

## <a name="see-also"></a>Confira também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)