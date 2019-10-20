---
title: DoWhile designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656768"
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile
A atividade de <xref:System.Activities.Statements.DoWhile> executa a atividade contida em seu <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma condição especificada seja avaliada como **falsa**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.DoWhile> e descreve como usá-los no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|A atividade a ser executada enquanto a condição é **verdadeira**. Para adicionar a atividade de <xref:System.Activities.Statements.DoWhile.Body%2A>, descarte uma atividade da caixa de ferramentas para o **corpo** de atividade no designer de atividades **DoWhile** com o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir o <xref:System.Activities.Statements.DoWhile.Condition%2A>, digite uma expressão de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] na caixa **condição** no designer de atividade **DoWhile** ou na grade de propriedades.|

## <a name="see-also"></a>Consulte também
 [Enquanto](../workflow-designer/while-activity-designer.md) o [fluxo de controle](../workflow-designer/control-flow-activity-designers.md)