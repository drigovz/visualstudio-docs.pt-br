---
title: Designer de modelos ReceiveAndSendReply | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.ReceiveAndSendReply.UI
- System.ServiceModel.Activities.SendReply.UI
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4c00eed244867cfd38b20f6a8f065fc6da006801
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395388"
---
# <a name="receiveandsendreply-template-designer"></a>Designer do modelo de ReceiveAndSendReply
O modelo **ReceiveAndSendReply** é usado para criar um par de predefinidos <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> atividades em uma <xref:System.Activities.Statements.Sequence> atividade que são correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no servidor.

## <a name="the-receiveandsendreply-template"></a>O modelo de ReceiveAndSendReply
 A adição do modelo **ReceiveAndSendReply** faz três coisas além da criação das <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> atividades e com uma <xref:System.Activities.Statements.Sequence> atividade:

1. Configurar <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> .

2. Associa a propriedade de <xref:System.ServiceModel.Activities.SendReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> a atividade de <xref:System.ServiceModel.Activities.Send> .

3. Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="using-the-receiveandsendreply-template-designer"></a>Usando o designer do modelo de ReceiveAndSendReply
 O designer de atividade **ReceiveAndSendReply** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** em [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade do **ReceiveAndSendReply** pode ser arrastado da **caixa de ferramentas** e descartado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície sempre que as atividades são geralmente colocadas. Isso cria uma <xref:System.ServiceModel.Activities.Receive> atividade que pode ser configurada com o designer de atividade de **envio** e uma correlacionada <xref:System.ServiceModel.Activities.SendReply> que pode ser configurada com o designer de SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando o designer de **recebimento** para configurar a <xref:System.ServiceModel.Activities.Receive> atividade, consulte o tópico [receber](../workflow-designer/receive-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando o designer do **SendReplyToReceive** para configurar a <xref:System.ServiceModel.Activities.SendReply> atividade, consulte a seção a seguir.

### <a name="properties-of-sendreply"></a>Propriedades de SendReply
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.SendReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e alguns podem ser editados na superfície do designer de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|                               Nome da propriedade                                | Obrigatório |                                                                                                                                                                                                                                                                                                                                                      Uso                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Falso   |                                                                                                                                                                                            O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.SendReply> . O padrão é SendReplyToReceive.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   Verdadeiro   | Fazer referência a <xref:System.ServiceModel.Activities.Receive> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.SendReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> as atividades são usadas em conjunto no servidor para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.SendReply> . |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Falso   |                       Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de elipse ao lado do campo **conteúdo** na grade de propriedades ou clicando em **definir...** botão ao lado do rótulo de **conteúdo** na superfície do designer de atividade **Receive** . Ambos exibem a caixa de diálogo **definição de conteúdo** . [!INCLUDE[crabout](../includes/crabout-md.md)] como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) .                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Falso   |            Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . [!INCLUDE[crabout](../includes/crabout-md.md)] usando essa caixa, consulte o tópico [Adicionar CorrelationInitializers da caixa de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md) .            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Falso   |                                                                                                                                                                                                                                              Especifica o cabeçalho da ação de mensagem. Se não é explicitamente definida, seu valor por padrão:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Falso   |                                                                                                                                                                                                                                                                                          Especifica se a instância de fluxo de trabalho deve ser persistentes antes que a mensagem de resposta que é enviada. O valor padrão é **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Consulte Também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [receber](../workflow-designer/receive-activity-designer.md) [Enviar](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)