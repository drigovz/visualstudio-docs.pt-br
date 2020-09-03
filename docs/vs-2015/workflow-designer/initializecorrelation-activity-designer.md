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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659015"
---
# <a name="initializecorrelation-activity-designer"></a>Designer de atividade de InitializeCorrelation
O designer de atividade **InitializeCorrelation** é usado para criar e configurar uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade que é usada para estabelecer uma correlação entre as mensagens antes de enviá-las ou recebê-las.

## <a name="the-initializecorrelation-activity"></a>A atividade de InitializeCorrelation
 Uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> é usada para inicializar correlações sem enviar e receber uma mensagem. Correlação é inicializada normalmente ao enviar ou para receber uma mensagem. Se correlação deve ser estabelecida antes que uma mensagem ser enviada ou recebida, use <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar correlação.

### <a name="using-the-initializecorrelation-activity-designer"></a>Usando o designer de atividade de InitializeCorrelation
 O designer de atividade **InitializeCorrelation** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade do **InitializeCorrelation** pode ser arrastado da **caixa de ferramentas** e retirado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície. Isso cria uma <xref:System.ServiceModel.Activities.InitializeCorrelation> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de InitializeCorrelation. o <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade do **InitializeCorrelation** ou na caixa **DisplayName** da janela **Propriedades** .

 O <xref:System.ServiceModel.Activities.CorrelationHandle> pode ser especificado no campo **correlação** na janela **Propriedades** na superfície do designer de atividade do **InitializeCorrelation** .

 Clicando no botão de reticências além do campo **CorrelationData** na janela **Propriedades** ou na "exibição..." texto de dica na superfície do designer de atividade do **InitializeCorrelation** exibe a caixa de diálogo **inicializar correlação** na qual você pode especificar o identificador de correlação e os pares chave-valor usados para inicializá-lo. [!INCLUDE[crabout](../includes/crabout-md.md)] usando essa caixa de diálogo, consulte o tópico da [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>As propriedades de InitializeCorrelation
 A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.InitializeCorrelation> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na janela **Propriedades** ou na [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície.

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> . O valor padrão é InitializeCorrelation.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|Falso|<xref:System.ServiceModel.Activities.CorrelationHandle> usado para associar atividades de fluxo de trabalho em correlação.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|Falso|Um dicionário de dados de correlação que se relacionam mensagens ao fluxo de trabalho instância.<br /><br /> Use a caixa de diálogo **inicializar correlação** para configurar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> . [!INCLUDE[crabout](../includes/crabout-md.md)] Use essa caixa de diálogo para ver o tópico [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Consulte Também
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [receber](../workflow-designer/receive-activity-designer.md) [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) [Enviar](../workflow-designer/send-activity-designer.md) [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)