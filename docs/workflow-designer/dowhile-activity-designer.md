---
title: Designer de fluxo de trabalho - Designer de atividade DoWhile
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a674cf58740fe914d00ae1ebfdeb5b642716e37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960549"
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile

O <xref:System.Activities.Statements.DoWhile> atividade executa a atividade contida em seu <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma condição especificada for avaliada como **falso**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho

A tabela a seguir mostra os mais úteis <xref:System.Activities.Statements.DoWhile> propriedades da atividade e descreve como usá-los no designer:

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|A atividade a executar quando a condição for **verdadeira**. Para adicionar o <xref:System.Activities.Statements.DoWhile.Body%2A> atividade, soltar uma atividade na caixa de ferramentas para o **corpo** caixa no **DoWhile** designer de atividade com o texto de dica "Descartar atividade aqui".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir a <xref:System.Activities.Statements.DoWhile.Condition%2A>, digite uma expressão do Visual Basic na **condição** caixa no **DoWhile** atividade designer ou na grade de propriedade.|

## <a name="see-also"></a>Consulte também

- [While](../workflow-designer/while-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)