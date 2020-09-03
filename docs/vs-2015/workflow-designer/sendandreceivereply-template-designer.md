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
ms.openlocfilehash: 1bfe43f410709a924b0ebdb0cf6afbb8d30a8fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395336"
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply
O modelo **SendAndReceiveReply** é usado para criar um par de predefinidos <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> atividades em uma <xref:System.Activities.Statements.Sequence> atividade que são correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no cliente.

## <a name="the-sendandreceivereply-template"></a>O modelo de SendAndReceiveReply
 A adição do modelo **SendAndReceiveReply** faz três coisas além da criação das <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> atividades e dentro de uma <xref:System.Activities.Statements.Sequence> atividade:

1. Configurar <xref:System.ServiceModel.Activities.Send.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Send> .

2. Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .

3. Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="using-the-sendandreceivereply-template-designer"></a>Usando o designer do modelo de SendAndReceiveReply
 O designer de atividade **SendAndReceiveReply** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** em [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade do **SendAndReceiveReply** pode ser arrastado da **caixa de ferramentas** e descartado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície sempre que as atividades são geralmente colocadas. Isso cria uma <xref:System.ServiceModel.Activities.Send> atividade que pode ser configurada com o designer de atividade de **envio** e uma correlacionada <xref:System.ServiceModel.Activities.ReceiveReply> que pode ser configurada com o designer de **ReceiveReplyForSend** .

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando o designer de **envio** para configurar a <xref:System.ServiceModel.Activities.Send> atividade, consulte o tópico [Enviar](../workflow-designer/send-activity-designer.md) .

 [!INCLUDE[crabout](../includes/crabout-md.md)] usando o designer do **ReceiveReplyForSend** para configurar a <xref:System.ServiceModel.Activities.ReceiveReply> atividade, consulte a seção a seguir.

### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.ReceiveReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas podem ser editadas na [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície do designer.

|                                 Nome da propriedade                                 | Obrigatório |                                                                                                                                                                                                                                                                                                                                                        Uso                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  Falso   |                                                                                                                                                                                            O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   Verdadeiro   | Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Essa propriedade não deve ser **nula**. <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.ReceiveReply> as atividades são usadas em conjunto no cliente para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  Falso   |                        Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade clicando no botão de elipse ao lado do campo **conteúdo** na grade de propriedades ou clicando em **definir...** botão ao lado do rótulo de **conteúdo** na superfície do designer de atividade **Receive** . Ambos exibem a caixa de diálogo **definição de conteúdo** . [!INCLUDE[crabout](../includes/crabout-md.md)] como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) .                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  Falso   |              Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . [!INCLUDE[crabout](../includes/crabout-md.md)] usando essa caixa, consulte o tópico [Adicionar CorrelationInitializers da caixa de diálogo](../workflow-designer/add-correlationinitializers-dialog-box.md) .               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  Falso   |                                                                                                                                                                                                                                               Especifica o cabeçalho da ação de mensagem. Se não é explicitamente definida, seu valor por padrão:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Consulte Também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [receber](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Enviar](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)