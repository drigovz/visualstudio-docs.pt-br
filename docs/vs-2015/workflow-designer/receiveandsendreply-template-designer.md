---
title: Designer de modelos receiveandsendreply | Microsoft Docs
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
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395388"
---
# <a name="receiveandsendreply-template-designer"></a>Designer do modelo de ReceiveAndSendReply
O modelo **ReceiveAndSendReply** é usado para criar <xref:System.ServiceModel.Activities.Receive> um <xref:System.ServiceModel.Activities.SendReply> par <xref:System.Activities.Statements.Sequence> de atividades pré-configuradas dentro de uma atividade que estão correlacionadas como parte de um padrão de troca de mensagens de solicitação/resposta no servidor.

## <a name="the-receiveandsendreply-template"></a>O modelo de ReceiveAndSendReply
 Adicionar o modelo **ReceiveAndSendReply** faz <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> três coisas <xref:System.Activities.Statements.Sequence> além de criar as atividades com uma atividade:

1. Configurar <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, propriedades de <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> .

2. Associa a propriedade de <xref:System.ServiceModel.Activities.SendReply.Request%2A> de atividade de <xref:System.ServiceModel.Activities.Receive> a atividade de <xref:System.ServiceModel.Activities.Send> .

3. Cria <xref:System.ServiceModel.Activities.CorrelationHandle> como um variável na atividade pai.

### <a name="using-the-receiveandsendreply-template-designer"></a>Usando o designer do modelo de ReceiveAndSendReply
 O designer de atividades **ReceiveAndSendReply** pode ser encontrado na categoria **Mensagens** da Caixa de [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Ferramentas**, que é acessada clicando na guia Caixa de **ferramentas** (Alternativamente, selecione Barra de **ferramentas** no menu **Exibir** ou CTRL+ALT+X.)

 O designer de atividades **ReceiveAndSendReply** pode ser arrastado da [!INCLUDE[wfd2](../includes/wfd2-md.md)] caixa de **ferramentas** e jogado sobre a superfície onde as atividades geralmente são colocadas. Isso cria <xref:System.ServiceModel.Activities.Receive> uma atividade que pode ser configurada com <xref:System.ServiceModel.Activities.SendReply> o designer de atividades **Send** e uma correlacionada que pode ser configurada com o designer SendReplyToReceive.

 [!INCLUDE[crabout](../includes/crabout-md.md)]usando o **designer Receber** <xref:System.ServiceModel.Activities.Receive> para configurar a atividade, consulte o tópico [Receber.](../workflow-designer/receive-activity-designer.md)

 [!INCLUDE[crabout](../includes/crabout-md.md)]usando o **designer SendReplyToReceive** <xref:System.ServiceModel.Activities.SendReply> para configurar a atividade, consulte a seção a seguir.

### <a name="properties-of-sendreply"></a>Propriedades de SendReply
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.SendReply> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e alguns podem ser editados na superfície do designer de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|                               Nome da propriedade                                | Obrigatório |                                                                                                                                                                                                                                                                                                                                                      Uso                                                                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              <xref:System.Activities.Activity.DisplayName%2A>              |  Falso   |                                                                                                                                                                                            O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.SendReply> . O padrão é SendReplyToReceive.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.                                                                                                                                                                                             |
|         <xref:System.ServiceModel.Activities.SendReply.Request%2A>         |   True   | Fazer referência a <xref:System.ServiceModel.Activities.Receive> a atividade emparelhada com esta atividade de <xref:System.ServiceModel.Activities.SendReply> . Esta propriedade não deve ser **nula.** <xref:System.ServiceModel.Activities.Receive>e <xref:System.ServiceModel.Activities.SendReply> as atividades são usadas em conjunto no servidor para modelar um padrão de mensagens de solicitação/resposta. Esta propriedade especifica que a atividade de <xref:System.ServiceModel.Activities.Send> é emparelhada. No designer, você não pode editar esta propriedade como é associada automaticamente a atividade de <xref:System.ServiceModel.Activities.Send> de que você criou a atividade de <xref:System.ServiceModel.Activities.SendReply> . |
|         <xref:System.ServiceModel.Activities.SendReply.Content%2A>         |  Falso   |                       Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite esta propriedade clicando no botão elipse ao lado do campo **Conteúdo** na grade de propriedades ou clicando em **Definir...** botão ao lado da etiqueta **Conteúdo** na superfície do designer **de atividades Receber.** Ambos exibem a caixa de diálogo Definição de **conteúdo.** [!INCLUDE[crabout](../includes/crabout-md.md)]como usar esta caixa, consulte o tópico [Caixa de Diálogo de Definição de Conteúdo.](../workflow-designer/content-definition-dialog-box.md)                       |
| <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> |  Falso   |            Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão elipse <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> ao lado da propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar iniciadores de correlação.** [!INCLUDE[crabout](../includes/crabout-md.md)]usando esta caixa, consulte o tópico [Caixa de diálogo Adicionar correlaçãoInicializadores.](../workflow-designer/add-correlationinitializers-dialog-box.md)            |
|         <xref:System.ServiceModel.Activities.SendReply.Action%2A>          |  Falso   |                                                                                                                                                                                                                                              Especifica o cabeçalho da ação de mensagem. Se não é explicitamente definida, seu valor por padrão:<br /><br /> `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`                                                                                                                                                                                                                                              |
|    <xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>    |  Falso   |                                                                                                                                                                                                                                                                                          Especifica se a instância de fluxo de trabalho deve ser persistentes antes que a mensagem de resposta que é enviada. O valor padrão é **false**.                                                                                                                                                                                                                                                                                           |

## <a name="see-also"></a>Consulte também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [SendAndReceive](../workflow-designer/send-activity-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)