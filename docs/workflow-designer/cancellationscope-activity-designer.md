---
title: Designer de atividade Designer de Fluxo de Trabalho-CancellationScope
description: Saiba como você pode usar o designer de atividade CancellationScope para criar e configurar uma atividade CancellationScope.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 746ed70d0a1a8ae4de2207ea1fdf15280bd44de9
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434435"
---
# <a name="cancellationscope-activity-designer"></a>Designer de atividade de CancellationScope

O designer de atividade **CancellationScope** é usado para criar e configurar uma <xref:System.Activities.Statements.CancellationScope> atividade.

## <a name="the-cancellationscope-activity"></a>A atividade de CancellationScope

A atividade de <xref:System.Activities.Statements.CancellationScope> permite que você especifique uma atividade para a lógica de execução e cancelar para a atividade.

### <a name="using-the-cancellationscope-activity-designer"></a>Usando o designer de atividade de CancellationScope

O designer de atividade **CancellationScope** pode ser encontrado na categoria **transação** da **caixa de ferramentas**. Para abrir a **caixa de ferramentas** , selecione a guia caixa de **ferramentas** do designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

O designer de atividade do **CancellationScope** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde as atividades são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade **CancellationScope** cria uma <xref:System.Activities.Statements.CancellationScope> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de CancellationScope. Edite o <xref:System.Activities.Activity.DisplayName%2A> valor no cabeçalho do designer de atividade **CancellationScope** . Você também pode editá-lo na caixa **DisplayName** da grade de propriedades.

### <a name="the-cancellationscope-properties"></a>As propriedades de CancellationScope

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer. A <xref:System.Activities.Activity.DisplayName%2A> propriedade pode ser editada na grade de propriedades, mas as outras propriedades devem ser editadas na superfície designer de fluxo de trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CancellationScope> . O padrão é CancellationScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Verdadeiro|Especifica a atividade para que a lógica cancelar é fornecida. Para adicionar a <xref:System.Activities.Statements.CancellationScope.Body%2A> atividade, descartar uma atividade da caixa de **ferramentas** no **corpo** box no designer de atividade do **CancellationScope** . Adicione o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Verdadeiro|Especifica a atividade que é executada se houver um cancelamento. Para adicionar a <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> atividade, descarte uma atividade da caixa de **ferramentas** no **CancellationHandler** box no designer de atividade do **CancellationScope** . Adicione o texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Confira também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [Veja](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
