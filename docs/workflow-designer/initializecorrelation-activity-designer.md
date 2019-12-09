---
title: Designer de atividade Designer de Fluxo de Trabalho-InitializeCorrelation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98a9a6bccb6eab2c4565a717daa897f93dbe8f53
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650219"
---
# <a name="initializecorrelation-activity-designer"></a>Designer de atividade de InitializeCorrelation

O designer de atividade **InitializeCorrelation** é usado para criar e configurar uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation>. A atividade <xref:System.ServiceModel.Activities.InitializeCorrelation> estabelece uma correlação entre as mensagens antes de enviá-las ou recebê-las.

## <a name="the-initializecorrelation-activity"></a>A atividade de InitializeCorrelation

Uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> é usada para inicializar correlações sem enviar e receber uma mensagem. Correlação é inicializada normalmente ao enviar ou para receber uma mensagem. Se correlação deve ser estabelecida antes que uma mensagem ser enviada ou recebida, use <xref:System.ServiceModel.Activities.InitializeCorrelation> para inicializar correlação.

### <a name="using-the-initializecorrelation-activity-designer"></a>Usando o designer de atividade de InitializeCorrelation

Acesse o designer de atividades do **InitializeCorrelation** na categoria **mensagens** da **caixa de ferramentas**.

O designer de atividade do **InitializeCorrelation** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de designer de fluxo de trabalho. Descartar o designer de atividade cria uma atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> com uma <xref:System.Activities.Activity.DisplayName%2A> padrão de InitializeCorrelation. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **InitializeCorrelation** ou na caixa **DisplayName** da janela **Propriedades** .

O <xref:System.ServiceModel.Activities.CorrelationHandle> pode ser especificado no campo **correlação** na janela **Propriedades** na superfície do designer de atividade **InitializeCorrelation** .

Para exibir a caixa de diálogo **inicializar correlação** , em que você pode especificar o identificador de correlação e os pares chave-valor usados para inicializá-lo, selecione o botão de reticências ao lado do campo **CorrelationData** na janela **Propriedades** . Ou então, selecione o botão "Exibir..." texto de dica na superfície do designer de atividade do **InitializeCorrelation** . Para obter mais informações sobre como usar essa caixa de diálogo, consulte o artigo [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>As propriedades de InitializeCorrelation

A tabela a seguir mostra as propriedades <xref:System.ServiceModel.Activities.InitializeCorrelation> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na janela **Propriedades** ou na superfície designer de fluxo de trabalho.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> . O valor padrão é InitializeCorrelation.<br /><br /> Embora o uso de um valor não padrão para a <xref:System.Activities.Activity.DisplayName%2A> amigável não seja estritamente necessário, é recomendável.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> usado para associar atividades de fluxo de trabalho em correlação.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Um dicionário de dados de correlação que se relacionam mensagens ao fluxo de trabalho instância.<br /><br /> Use a caixa de diálogo **inicializar correlação** para configurar o <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Para obter mais informações sobre como usar essa caixa de diálogo, consulte o artigo [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Consulte também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)