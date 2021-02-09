---
title: Designer de Fluxo de Trabalho-se designer de atividade
description: Saiba como a atividade If avalia uma condição e executa uma atividade dependendo dos resultados dessa avaliação.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93f36a3c2b587718fe6889688baa50224f663c1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881354"
---
# <a name="if-activity-designer"></a>Se designer de atividades

A atividade de <xref:System.Activities.Statements.If> avalia uma condição e executa uma atividade dependendo dos resultados da avaliação. Esta atividade é mais útil ao usar um estilo modelando procedural de programação. Uma atividade de <xref:System.Activities.Statements.If> pode ser aninhadas dentro de uma atividade de <xref:System.Activities.Statements.Sequence> ou uma atividade de <xref:System.Activities.Statements.Parallel> , por exemplo. Se você estiver usando uma atividade de <xref:System.Activities.Statements.Flowchart> , considere usar uma atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.

## <a name="if-properties-in-the-workflow-designer"></a>Se as propriedades em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.If> e descreve como usá-los no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|A condição que determina que atividade filho para executar. Para definir o <xref:System.Activities.Statements.If.Condition%2A> , digite uma expressão de Visual Basic na caixa **condição** no designer de atividade **If** ou na grade de propriedades.|
|<xref:System.Activities.Statements.If.Else%2A>|Falso|A atividade a ser executada se o <xref:System.Activities.Statements.If.Condition%2A> for **falso**. Para adicionar uma atividade que é executada pela <xref:System.Activities.Statements.If.Else%2A> ramificação, descarte uma atividade da caixa de **ferramentas** no  **caso** do designer de atividade, com texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.If.Then%2A>|Falso|A atividade a ser executada se o <xref:System.Activities.Statements.If.Condition%2A> for **verdadeiro**. Para adicionar uma atividade que é executada pela <xref:System.Activities.Statements.If.Then%2A> ramificação, descarte uma atividade da caixa de **ferramentas** no **em seguida** , no, **se** o designer de atividade com texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Confira também

- [Sequência](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
