---
title: Designer de Fluxo de Trabalho-se designer de atividade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 099be38c5585fe19c00b31c00ac3a7ddcd3d7fe2
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111468"
---
# <a name="if-activity-designer"></a>Se designer de atividades

A atividade de <xref:System.Activities.Statements.If> avalia uma condição e executa uma atividade dependendo dos resultados da avaliação. Esta atividade é mais útil ao usar um estilo modelando procedural de programação. Uma atividade de <xref:System.Activities.Statements.If> pode ser aninhadas dentro de uma atividade de <xref:System.Activities.Statements.Sequence> ou uma atividade de <xref:System.Activities.Statements.Parallel> , por exemplo. Se você estiver usando uma atividade de <xref:System.Activities.Statements.Flowchart> , considere usar uma atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.

## <a name="if-properties-in-the-workflow-designer"></a>Se as propriedades em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.If> e descreve como usá-los no designer.

|Nome da Propriedade|Necessário|Medição de|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|verdadeiro|A condição que determina que atividade filho para executar. Para definir o <xref:System.Activities.Statements.If.Condition%2A>, digite uma expressão de Visual Basic na caixa **condição** no designer de atividade **If** ou na grade de propriedades.|
|<xref:System.Activities.Statements.If.Else%2A>|False|A atividade a ser executada se a <xref:System.Activities.Statements.If.Condition%2A> for **falsa**. Para adicionar uma atividade que é executada pela ramificação de <xref:System.Activities.Statements.If.Else%2A>, descarte uma atividade da caixa de **ferramentas** no **else** , no **If** Activity Designer, com texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.If.Then%2A>|False|A atividade a ser executada se a <xref:System.Activities.Statements.If.Condition%2A> for **verdadeira**. Para adicionar uma atividade que é executada pela ramificação <xref:System.Activities.Statements.If.Then%2A>, descarte uma atividade da caixa de **ferramentas** em **seguida** no designer de atividade **If** com texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Veja também

- [Sequência](../workflow-designer/sequence-activity-designer.md)
- [Paralelo](../workflow-designer/parallel-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
