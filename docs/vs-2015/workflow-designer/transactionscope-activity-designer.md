---
title: Designer de atividade TransactionScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5a1d38ea37896cedcd2166c42f37ce037a1c4cd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670183"
---
# <a name="transactionscope-activity-designer"></a>Designer de atividade de TransactionScope
O designer de atividade **TransactionScope** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>A atividade de TransactionScope
 A atividade de <xref:System.Activities.Statements.TransactionScope> executa a atividade contida em uma única transação. As confirmações de transação quando a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A> e todos outros participantes na transação tiver terminado com êxito.

### <a name="using-the-transactionscope-activity-designer"></a>Usando o designer de atividade de TransactionScope
 O designer de atividade **TransactionScope** pode ser encontrado na categoria **transação** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** do [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** na **exibição** menu ou CTRL + ALT + X.)

 O designer de atividade **TransactionScope** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.TransactionScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TransactionScope. O valor <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **TransactionScope** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-transactionscope-properties"></a>As propriedades de TransactionScope
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TransactionScope> e descreve como elas são usadas no designer. As propriedades de <xref:System.Activities.Activity.DisplayName%2A> e de <xref:System.Activities.Statements.TransactionScope.Body%2A> podem ser editadas na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] . Mas as outras propriedades devem ser editadas na grade de propriedade.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.TransactionScope> . O padrão é TransactionScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Especifica a atividade para executar em uma única transação. Para adicionar a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A>, descarte uma atividade da caixa de **ferramentas** no **corpo** de atividade no **TransactionScope** Activity Designer com dica de texto "soltar atividade aqui".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Especifica <xref:System.Transactions.IsolationLevel> para este <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica o intervalo de tempo (formatados como o 00:00: 00, que indica horas: minutos: segundos) que a transação precisará concluir. O valor padrão é 1 (00:01 minuto: 00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure?qualifyHint=False&autoUpgrade=True>|True|Especifica o valor que indica se o fluxo de trabalho deve ser anuladas se a transação nulos.|

## <a name="see-also"></a>Consulte também
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md) [transação](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [compensar](../workflow-designer/compensate-activity-designer.md) [confirmação](../workflow-designer/confirm-activity-designer.md)