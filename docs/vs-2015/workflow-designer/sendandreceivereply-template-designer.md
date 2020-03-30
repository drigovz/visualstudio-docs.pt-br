---
title: SendandReceiveReply Model Designer | Microsoft Docs
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395336"
---
# <a name="sendandreceivereply-template-designer"></a>Designer do modelo de SendAndReceiveReply
O modelo **SendAndReceiveReply** é usado para criar <xref:System.ServiceModel.Activities.Send> um <xref:System.ServiceModel.Activities.ReceiveReply> par <xref:System.Activities.Statements.Sequence> de atividades pré-configuradas dentro de uma atividade que estão correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no cliente.

## <a name="the-sendandreceivereply-template"></a>O modelo de SendAndReceiveReply
 Adicionar o modelo **SendAndReceiveReply** faz <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> três coisas <xref:System.Activities.Statements.Sequence> além de criar as atividades dentro de uma atividade:

1. Configurar <xref:System.ServiceModel.Activities.Send.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Send> .

2. Associa a propriedade de <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> a atividade de <xref:System.ServiceModel.Activities.Send> .

3. Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="using-the-sendandreceivereply-template-designer"></a>Usando o designer do modelo de SendAndReceiveReply
 O designer de atividades **SendAndReceiveReply** pode ser encontrado na categoria **Mensagens** da Caixa de [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Ferramentas**, que é acessada clicando na guia **Caixa de ferramentas** (Alternativamente, selecione Barra de **ferramentas** no menu **Exibir** ou CTRL+ALT+X.)

 O designer de atividades **SendAndReceiveReply** pode ser arrastado da [!INCLUDE[wfd2](../includes/wfd2-md.md)] caixa de **ferramentas** e jogado sobre a superfície onde as atividades geralmente são colocadas. Isso cria <xref:System.ServiceModel.Activities.Send> uma atividade que pode ser configurada com <xref:System.ServiceModel.Activities.ReceiveReply> o designer de atividades **Send** e uma correlacionada que pode ser configurada com o designer **ReceiveReplyForSend.**

 [!INCLUDE[crabout](../includes/crabout-md.md)]usando o **desenhista Enviar** para configurar a <xref:System.ServiceModel.Activities.Send> atividade, consulte o tópico [Enviar.](../workflow-designer/send-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]usando o **designer ReceiveReplyForSend** <xref:System.ServiceModel.Activities.ReceiveReply> para configurar a atividade, consulte a seção a seguir.

### <a name="properties-of-receivereply"></a>Propriedades de ReceiveReply
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.ReceiveReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de [!INCLUDE[wfd2](../includes/wfd2-md.md)]propriedades e algumas podem ser editadas na superfície do designer.

|                                 Nome da propriedade                                 | Obrigatório |                                                                                                                                                                                                                                                                                                                                                        Uso                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------------------------------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|               <xref:System.Activities.Activity.DisplayName%2A>                |  Falso   |                                                                                                                                                                                            O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . O padrão é ReceiveReplyForSend.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.                                                                                                                                                                                            |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>         |   True   | Fazer referência a <xref:System.ServiceModel.Activities.Send> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . Esta propriedade não deve ser **nula.** <xref:System.ServiceModel.Activities.Send>e <xref:System.ServiceModel.Activities.ReceiveReply> as atividades são usadas em conjunto no cliente para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.ReceiveReply> . |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>         |  Falso   |                        Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite esta propriedade clicando no botão elipse ao lado do campo **Conteúdo** na grade de propriedades ou clicando em **Definir...** botão ao lado da etiqueta **Conteúdo** na superfície do designer **de atividades Receber.** Ambos exibem a caixa de diálogo Definição de **conteúdo.** [!INCLUDE[crabout](../includes/crabout-md.md)]como usar esta caixa, consulte o tópico [Caixa de Diálogo de Definição de Conteúdo.](../workflow-designer/content-definition-dialog-box.md)                         |
| <xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A> |  Falso   |              Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão elipse <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> ao lado da propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar iniciadores de correlação.** [!INCLUDE[crabout](../includes/crabout-md.md)]usando esta caixa, consulte o tópico [Caixa de diálogo Adicionar correlaçãoInicializadores.](../workflow-designer/add-correlationinitializers-dialog-box.md)               |
|         <xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>          |  Falso   |                                                                                                                                                                                                                                               Especifica o cabeçalho da ação de mensagem. Se não é explicitamente definida, seu valor por padrão:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`.                                                                                                                                                                                                                                              |

## <a name="see-also"></a>Consulte também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendSend](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)