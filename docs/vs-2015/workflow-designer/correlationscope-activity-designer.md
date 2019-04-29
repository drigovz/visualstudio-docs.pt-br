---
title: Designer de atividade de CorrelationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 95c8422d53903c3c7b81db9f6ef042c5ea9ff1c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976759"
---
# <a name="correlationscope-activity-designer"></a>Designer de atividade de CorrelationScope
O **CorrelationScope** designer de atividade é usado para criar e configurar um <xref:System.ServiceModel.Activities.CorrelationScope> atividade que fornece gerenciamento implícito de atividades filhos de mensagem usando um <xref:System.ServiceModel.Activities.CorrelationHandle> objeto.  
  
## <a name="the-correlationscope-activity"></a>A atividade de CorrelationScope  
 A propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. As atividades de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> contidas em <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> são configurados para usar a propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de atividade de conteúdo da <xref:System.ServiceModel.Activities.CorrelationScope> para executar correlação.  
  
### <a name="using-the-correlationscope-activity-designer"></a>Usando o designer de atividade de CorrelationScope  
 O **CorrelationScope** designer de atividade pode ser encontrado na **Messaging** categoria da **caixa de ferramentas**, que é acessado clicando o **dacaixadeferramentas** guia no lado esquerdo do [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** do **exibição** menu, ou CTRL + ALT + X.)  
  
 O **CorrelationScope** designer de atividade pode ser arrastado da **caixa de ferramentas** e ser solto sobre a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície. Isso cria uma <xref:System.ServiceModel.Activities.CorrelationScope> atividade com um padrão **DisplayName** de CorrelationScope. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **CorrelationScope** designer de atividade ou nos **DisplayName** caixa do **propriedades** janela.  
  
 Para especificar o <xref:System.ServiceModel.Activities.CorrelationHandle> usado por atividades filhos de mensagem, clique no botão de elipse ao lado de **CorrelatesWith** campo **propriedades** janela para exibir o **Editor de expressão**  caixa de diálogo. Esta propriedade pode também ser definida na superfície do designer de atividade.  
  
 As atividades no escopo dentro de correlação são especificadas soltando seus designers dentro de **corpo** caixa dentro a **CorrelationScope** designer.  
  
### <a name="the-correlationscope-properties"></a>As propriedades de CorrelationScope  
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.CorrelationScope> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na **propriedades** janela ou no [!INCLUDE[wfd2](../includes/wfd2-md.md)] designer surface e frequentemente em ambos.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> .|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. Se você não definir essa propriedade, <xref:System.ServiceModel.Activities.CorrelationScope><xref:System.ServiceModel.Activities.CorrelationHandle> implícito cria automaticamente.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica as atividades no escopo de correlação.|  
  
## <a name="see-also"></a>Consulte também  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Enviar](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)