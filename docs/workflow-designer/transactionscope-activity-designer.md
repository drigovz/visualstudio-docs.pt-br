---
title: Designer de atividade Designer de Fluxo de Trabalho TransactionScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef35457b9f28864929ad42919fff4e9afdcb0d5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114813"
---
# <a name="transactionscope-activity-designer"></a>Designer de atividade de TransactionScope

O designer de atividade **TransactionScope** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.TransactionScope>.

## <a name="the-transactionscope-activity"></a>A atividade de TransactionScope

A atividade de <xref:System.Activities.Statements.TransactionScope> executa a atividade contida em uma única transação. As confirmações de transação quando a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A> e todos outros participantes na transação tiver terminado com êxito.

### <a name="using-the-transactionscope-activity-designer"></a>Usando o designer de atividade de TransactionScope

Acesse o designer de atividade **TransactionScope** na categoria **transação** da **caixa de ferramentas**. O designer de atividade **TransactionScope** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.TransactionScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TransactionScope. O valor <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **TransactionScope** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-transactionscope-properties"></a>As propriedades de TransactionScope

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TransactionScope> e descreve como elas são usadas no designer. As propriedades <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Statements.TransactionScope.Body%2A> podem ser editadas na superfície Designer de Fluxo de Trabalho. Mas as outras propriedades devem ser editadas na grade de propriedade.

|Nome da Propriedade|Necessário|Medição de|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.TransactionScope> . O padrão é TransactionScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|verdadeiro|Especifica a atividade para executar em uma única transação. Para adicionar a atividade de <xref:System.Activities.Statements.TransactionScope.Body%2A>, descarte uma atividade da caixa de **ferramentas** no **corpo** de atividade no **TransactionScope** Activity Designer com dica de texto "soltar atividade aqui".|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|verdadeiro|Especifica <xref:System.Transactions.IsolationLevel> para este <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Especifica o intervalo de tempo (formatados como o 00:00: 00, que indica horas: minutos: segundos) que a transação precisará concluir. O valor padrão é 1 (00:01 minuto: 00).|
|[System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure](https://msdn.microsoft.com/library/system.activities.statements.transactionscope.abortinstanceontransactionfailure.aspx)|verdadeiro|Especifica o valor que indica se o fluxo de trabalho deve ser anuladas se a transação nulos.|

## <a name="see-also"></a>Veja também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
