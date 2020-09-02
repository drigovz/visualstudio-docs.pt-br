---
title: Designer de atividade do CorrelationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6ffcfd63d60ab6f085b5cb2a793e8bf17a50d8e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656921"
---
# <a name="correlationscope-activity-designer"></a>Designer de atividade de CorrelationScope
O designer de atividade **CorrelationScope** é usado para criar e configurar uma <xref:System.ServiceModel.Activities.CorrelationScope> atividade que fornece gerenciamento implícito de atividades de mensagens filho usando um <xref:System.ServiceModel.Activities.CorrelationHandle> objeto.

## <a name="the-correlationscope-activity"></a>A atividade de CorrelationScope
 A propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. As atividades de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> contidas em <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> são configurados para usar a propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de atividade de conteúdo da <xref:System.ServiceModel.Activities.CorrelationScope> para executar correlação.

### <a name="using-the-correlationscope-activity-designer"></a>Usando o designer de atividade de CorrelationScope
 O designer de atividade **CorrelationScope** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** no lado esquerdo da [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade do **CorrelationScope** pode ser arrastado da **caixa de ferramentas** e retirado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície. Isso cria uma <xref:System.ServiceModel.Activities.CorrelationScope> atividade com um **DisplayName** padrão de CorrelationScope. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **CorrelationScope** ou na caixa **DisplayName** da janela **Propriedades** .

 Para especificar o <xref:System.ServiceModel.Activities.CorrelationHandle> usado pelas atividades de mensagens filhas, clique no botão de reticências ao lado do campo **CorrelatesWith** na janela **Propriedades** para exibir a caixa de diálogo **Editor de expressão** . Esta propriedade pode também ser definida na superfície do designer de atividade.

 As atividades com escopo na correlação são especificadas descartando seus designers dentro da caixa do **corpo** no designer de **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>As propriedades de CorrelationScope
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.CorrelationScope> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na janela **Propriedades** ou na [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície do designer e, muitas vezes, em ambos.

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|Falso|Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. Se você não definir essa propriedade, <xref:System.ServiceModel.Activities.CorrelationScope><xref:System.ServiceModel.Activities.CorrelationHandle> implícito cria automaticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|Falso|Especifica as atividades no escopo de correlação.|

## <a name="see-also"></a>Consulte Também
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) [receber](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Enviar](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)