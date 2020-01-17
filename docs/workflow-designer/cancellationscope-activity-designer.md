---
title: Designer de atividade Designer de Fluxo de Trabalho-CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6d1067b529dffec5a4e6a1f21d5489c32311c07
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76112499"
---
# <a name="cancellationscope-activity-designer"></a>Designer de atividade de CancellationScope

O designer de atividade **CancellationScope** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>A atividade de CancellationScope

A atividade de <xref:System.Activities.Statements.CancellationScope> permite que você especifique uma atividade para a lógica de execução e cancelar para a atividade.

### <a name="using-the-cancellationscope-activity-designer"></a>Usando o designer de atividade de CancellationScope

O designer de atividade **CancellationScope** pode ser encontrado na categoria **transação** da **caixa de ferramentas**. Para abrir a **caixa de ferramentas**, selecione a guia caixa de **ferramentas** do designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl**+**ALT**+**X**.

O designer de atividade do **CancellationScope** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o designer de atividade **CancellationScope** cria uma atividade de <xref:System.Activities.Statements.CancellationScope> com um <xref:System.Activities.Activity.DisplayName%2A> padrão de CancellationScope. Edite o valor <xref:System.Activities.Activity.DisplayName%2A> no cabeçalho do designer de atividade **CancellationScope** . Você também pode editá-lo na caixa **DisplayName** da grade de propriedades.

### <a name="the-cancellationscope-properties"></a>As propriedades de CancellationScope

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer. A propriedade <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedades, mas as outras propriedades devem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da Propriedade|Necessário|Medição de|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CancellationScope> . O padrão é CancellationScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|verdadeiro|Especifica a atividade para que a lógica cancelar é fornecida. Para adicionar a atividade de <xref:System.Activities.Statements.CancellationScope.Body%2A>, descarte uma atividade da caixa de **ferramentas** no **corpo** do **CancellationScope** do designer de atividade. Adicione o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|verdadeiro|Especifica a atividade que é executada se houver um cancelamento. Para adicionar a atividade de <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, descarte uma atividade da caixa de **ferramentas** no **CancellationHandler** box no designer de atividade do **CancellationScope** . Adicione o texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Veja também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [Confirmar](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
