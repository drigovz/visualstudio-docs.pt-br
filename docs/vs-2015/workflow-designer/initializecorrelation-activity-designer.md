---
title: Designer de atividade do InitializeCorrelation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659015"
---
# <a name="initializecorrelation-activity-designer"></a>Designer de atividade de InitializeCorrelation
O designer de atividade do **InitializeCorrelation** é usado para criar e configurar uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> que é usada para estabelecer uma correlação entre as mensagens antes de enviá-las ou recebê-las.

## <a name="the-initializecorrelation-activity"></a>A atividade de InitializeCorrelation
 Uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> é usada para inicializar correlações sem enviar e receber uma mensagem. Correlação é inicializada normalmente ao enviar ou para receber uma mensagem. Se correlação deve ser estabelecida antes que uma mensagem ser enviada ou recebida, use <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar correlação.

### <a name="using-the-initializecorrelation-activity-designer"></a>Usando o designer de atividade de InitializeCorrelation
 O designer de atividade **InitializeCorrelation** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** na **exibição** menu ou CTRL + ALT + X.)

 O designer de atividade do **InitializeCorrelation** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)]. Isso cria uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> com um <xref:System.Activities.Activity.DisplayName%2A> padrão de InitializeCorrelation. o <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **InitializeCorrelation** ou na caixa **DisplayName** da janela **Propriedades** .

 O <xref:System.ServiceModel.Activities.CorrelationHandle> pode ser especificado no campo **correlação** na janela **Propriedades** na superfície do designer de atividade **InitializeCorrelation** .

 Clicando no botão de reticências além do campo **CorrelationData** na janela **Propriedades** ou na "exibição..." texto de dica na superfície do designer de atividade do **InitializeCorrelation** exibe a caixa de diálogo **inicializar correlação** na qual você pode especificar o identificador de correlação e os pares chave-valor usados para inicializá-lo. [!INCLUDE[crabout](../includes/crabout-md.md)] usando essa caixa de diálogo, consulte o tópico da [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>As propriedades de InitializeCorrelation
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.InitializeCorrelation> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na janela **Propriedades** ou na superfície [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> . O valor padrão é InitializeCorrelation.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usado para associar atividades de fluxo de trabalho em correlação.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Um dicionário de dados de correlação que se relacionam mensagens ao fluxo de trabalho instância.<br /><br /> Use a caixa de diálogo **inicializar correlação** para configurar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] usar essa caixa de diálogo, consulte o tópico da [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Consulte também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [receber](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Enviar](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)