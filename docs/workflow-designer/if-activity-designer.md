---
title: Designer de fluxo de trabalho - se o Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f069da9bb84074544cc388ab2bf7fa1eab3c7595
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917153"
---
# <a name="if-activity-designer"></a>Se designer de atividades

A atividade de <xref:System.Activities.Statements.If> avalia uma condição e executa uma atividade dependendo dos resultados da avaliação. Esta atividade é mais útil ao usar um estilo modelando procedural de programação. Uma atividade de <xref:System.Activities.Statements.If> pode ser aninhadas dentro de uma atividade de <xref:System.Activities.Statements.Sequence> ou uma atividade de <xref:System.Activities.Statements.Parallel> , por exemplo. Se você estiver usando uma atividade de <xref:System.Activities.Statements.Flowchart> , considere usar uma atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.

## <a name="if-properties-in-the-workflow-designer"></a>Se as propriedades em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.If> e descreve como usá-los no designer.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|verdadeiro|A condição que determina que atividade filho para executar. Para definir a <xref:System.Activities.Statements.If.Condition%2A>, digite uma expressão do Visual Basic na **condição** caixa no **se** atividade designer ou na grade de propriedade.|
|<xref:System.Activities.Statements.If.Else%2A>|False|A atividade a executar se a <xref:System.Activities.Statements.If.Condition%2A> está **falso**. Para adicionar uma atividade que é executada pelo <xref:System.Activities.Statements.If.Else%2A> ramificar, soltar uma atividade do **caixa de ferramentas** para o **Else** caixa no **se** designer de atividade com o texto de dica " Soltar atividade aqui".|
|<xref:System.Activities.Statements.If.Then%2A>|False|A atividade a executar se a <xref:System.Activities.Statements.If.Condition%2A> está **verdadeiro**. Para adicionar uma atividade que é executada pelo <xref:System.Activities.Statements.If.Then%2A> ramificar, soltar uma atividade do **caixa de ferramentas** para o **, em seguida,** caixa no **se** designer de atividade com o texto de dica " Soltar atividade aqui".|

## <a name="see-also"></a>Consulte também

- [Sequência](../workflow-designer/sequence-activity-designer.md)
- [Paralelo](../workflow-designer/parallel-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)