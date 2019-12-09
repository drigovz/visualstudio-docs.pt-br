---
title: Designer de Fluxo de Trabalho-o designer de atividade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650524"
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile

A atividade de <xref:System.Activities.Statements.DoWhile> executa a atividade contida em seu <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma condição especificada seja avaliada como **falsa**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de atividade de <xref:System.Activities.Statements.DoWhile> mais úteis e descreve como usá-las no designer:

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|A atividade a ser executada enquanto a condição é **verdadeira**. Para adicionar a atividade de <xref:System.Activities.Statements.DoWhile.Body%2A>, descarte uma atividade da caixa de ferramentas para o **corpo** de atividade no designer de atividades **DoWhile** com o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir o <xref:System.Activities.Statements.DoWhile.Condition%2A>, digite uma expressão de Visual Basic na caixa **condição** no designer de atividade **DoWhile** ou na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [While](../workflow-designer/while-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)