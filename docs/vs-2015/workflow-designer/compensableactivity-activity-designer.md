---
title: Designer de atividade do CompensableActivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656987"
---
# <a name="compensableactivity-activity-designer"></a>Designer de atividade de CompensableActivity
O designer de atividade **CompensableActivity** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>A atividade de CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> define uma unidade de trabalho que pode ser compensado confirmada ou após a conclusão com êxito.

### <a name="using-the-compensableactivity-activity-designer"></a>Usando o designer de atividade de CompensableActivity
 O designer de atividade do **CompensableActivity** pode ser encontrado na categoria **transação** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** no lado esquerdo da [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione barra de **ferramentas** no menu **Exibir** , ou CTRL + ALT + X.)

 O designer de atividade do **CompensableActivity** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.CompensableActivity> com <xref:System.Activities.Activity.DisplayName%2A> padrão de CompensableActivity. O valor <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **CompensableActivity** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-compensableactivity-properties"></a>As propriedades de CompensableActivity
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CompensableActivity> e descreve como elas são usadas no designer. A propriedade de <xref:System.Activities.Activity.DisplayName%2A> e de <xref:System.Activities.Activity%601.Result%2A> pode ser editada na grade de propriedade mas outras propriedades devem ser editadas na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CompensableActivity> . O padrão é CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Especifica o valor de retorno de <xref:System.Activities.Statements.CompensableActivity>. Esta propriedade deve ser editada na grade de propriedade.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Especifica a atividade para que a compensação, cancelamento, e a lógica de confirmação são fornecidos. Para adicionar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A>, descarte uma atividade da caixa de **ferramentas** no **corpo** do **CompensableActivity** do designer de atividades com dica de texto "soltar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Especifica a atividade que é executado no caso de cancelamento. Para adicionar a atividade, remova seu designer da caixa de **ferramentas** para o **CancellationHandler** box no designer de atividades do **CompensableActivity** com o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Especifica a atividade a ser executada para compensar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Compensate> .<br /><br /> Para adicionar a atividade, solte seu designer de atividade da caixa de **ferramentas** na **CompensationHandler** box no designer de atividades do **CompensableActivity** com o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Especifica a atividade a ser executada para confirmar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Confirm> .<br /><br /> Para adicionar a atividade, solte seu designer de atividade da caixa de **ferramentas** na **ConfirmationHandler** box no designer de atividades do **CompensableActivity** com o texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Consulte também
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) de [Compensate](../workflow-designer/compensate-activity-designer.md) [confirmação](../workflow-designer/confirm-activity-designer.md) de [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) de [transação](../workflow-designer/transaction-activity-designers.md)