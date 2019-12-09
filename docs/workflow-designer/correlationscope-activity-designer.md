---
title: Designer de atividade Designer de Fluxo de Trabalho-CorrelationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.CorrelationScope.UI
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d65e481342f7b7e86b3ce073b7d6a15254ae72d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650589"
---
# <a name="correlationscope-activity-designer"></a>Designer de atividade de CorrelationScope

O designer de atividade **CorrelationScope** é usado para criar e configurar uma atividade de <xref:System.ServiceModel.Activities.CorrelationScope> que fornece gerenciamento implícito de atividades de mensagens filho usando um objeto <xref:System.ServiceModel.Activities.CorrelationHandle>.

## <a name="the-correlationscope-activity"></a>A atividade CorrelationScope

A propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. As atividades de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> contidas em <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> são configurados para usar a propriedade de <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> de atividade de conteúdo da <xref:System.ServiceModel.Activities.CorrelationScope> para executar correlação.

### <a name="use-the-correlationscope-activity-designer"></a>Usar o designer de atividade do CorrelationScope

O designer de atividade **CorrelationScope** pode ser encontrado na categoria **mensagens** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** no lado esquerdo da designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** +**ALT** +**X**.

O designer de atividade do **CorrelationScope** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de designer de fluxo de trabalho. Isso cria uma atividade de <xref:System.ServiceModel.Activities.CorrelationScope> com um **DisplayName** padrão de CorrelationScope. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **CorrelationScope** ou na caixa **DisplayName** da janela **Propriedades** .

Para especificar o <xref:System.ServiceModel.Activities.CorrelationHandle> usado pelas atividades de mensagens filho, selecione o botão de reticências ao lado do campo **CorrelatesWith** na janela **Propriedades** para exibir a caixa de diálogo **Editor de expressão** . Esta propriedade pode também ser definida na superfície do designer de atividade.

As atividades com escopo na correlação são especificadas descartando seus designers dentro da caixa do **corpo** no designer de **CorrelationScope** .

### <a name="the-correlationscope-properties"></a>As propriedades CorrelationScope

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.CorrelationScope> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na janela **Propriedades** ou na superfície designer de fluxo de trabalho e, muitas vezes, em ambos.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.InitializeCorrelation> .|
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para gerenciar atividades filhos de mensagem. Se você não definir essa propriedade, <xref:System.ServiceModel.Activities.CorrelationScope><xref:System.ServiceModel.Activities.CorrelationHandle> implícito cria automaticamente.|
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Especifica as atividades no escopo de correlação.|

## <a name="see-also"></a>Consulte também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)