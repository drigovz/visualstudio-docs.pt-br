---
title: Designer do modelo de ReceiveAndSendReply
description: Saiba como usar o modelo ReceiveAndSendReply em Designer de Fluxo de Trabalho para criar um par de atividades de recebimento e SendReply pré-configuradas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bc86aed1e135f369d771a9ac47513c4eb28ce25
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926534"
---
# <a name="receiveandsendreply-template-designer"></a>Designer do modelo de ReceiveAndSendReply

O modelo **ReceiveAndSendReply** é usado para criar um par de atividades pré-configuradas e predefinidas <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> . As atividades fazem parte de uma <xref:System.Activities.Statements.Sequence> atividade e são correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no servidor.

## <a name="the-receiveandsendreply-template"></a>O modelo ReceiveAndSendReply

Adicionar um modelo **ReceiveAndSendReply** faz três coisas além da criação <xref:System.ServiceModel.Activities.Receive> das <xref:System.ServiceModel.Activities.SendReply> atividades e com uma <xref:System.Activities.Statements.Sequence> atividade:

- Configura as <xref:System.ServiceModel.Activities.Receive.OperationName%2A> <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> Propriedades e da <xref:System.ServiceModel.Activities.Receive> atividade.

- Associa a propriedade de <xref:System.ServiceModel.Activities.SendReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> a atividade de <xref:System.ServiceModel.Activities.Send> .

- Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="use-the-receiveandsendreply-template-designer"></a>Usar o designer de modelos ReceiveAndSendReply

Acesse o designer de atividades do **ReceiveAndSendReply** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade do **ReceiveAndSendReply** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. Descartar o designer de atividade cria uma <xref:System.ServiceModel.Activities.Receive> atividade que pode ser configurada com o designer de atividade de **envio** e uma correlacionada <xref:System.ServiceModel.Activities.SendReply> que pode ser configurada com o designer de SendReplyToReceive.

Para obter mais informações sobre como usar o designer de **recebimento** para configurar a <xref:System.ServiceModel.Activities.Receive> atividade, consulte [receber designer de atividade](../workflow-designer/receive-activity-designer.md).

### <a name="properties-of-sendreply"></a>Propriedades de SendReply

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.SendReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na superfície de Designer de Fluxo de Trabalho.

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.SendReply> . O padrão é SendReplyToReceive.<br /><br /> Embora o uso de um valor não padrão para o amigável <xref:System.Activities.Activity.DisplayName%2A> não seja estritamente necessário, é melhor usar esse valor. |
| <xref:System.ServiceModel.Activities.SendReply.Request%2A> | True | Fazer referência a <xref:System.ServiceModel.Activities.Receive> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.SendReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> as atividades são usadas em conjunto no servidor para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar essa propriedade porque ela é associada automaticamente à <xref:System.ServiceModel.Activities.Send> atividade da qual você criou a <xref:System.ServiceModel.Activities.SendReply> atividade. |
| <xref:System.ServiceModel.Activities.SendReply.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de reticências ao lado do campo **conteúdo** na grade de propriedades ou clicando no botão **definir** ao lado do rótulo **conteúdo** na superfície **receber** designer de atividade. Ambos exibem a caixa de diálogo **definição de conteúdo** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.SendReply.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se não estiver definido explicitamente, seu valor padrão será:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` |
| <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A> | Falso | Especifica se a instância de fluxo de trabalho deve ser persistentes antes que a mensagem de resposta que é enviada. O valor padrão é **false**. |

## <a name="see-also"></a>Confira também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recebe](../workflow-designer/receive-activity-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)