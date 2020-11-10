---
title: Designer de Fluxo de Trabalho-o designer de atividade
description: Saiba como a atividade DoWhile executa a atividade contida em seu corpo pelo menos uma vez, até que uma condição especificada seja avaliada como falsa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385fe376f56738d76e066dc172e7b6b516f9a08
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438055"
---
# <a name="dowhile-activity-designer"></a>Designer de atividade DoWhile

A <xref:System.Activities.Statements.DoWhile> atividade executa a atividade contida em <xref:System.Activities.Statements.DoWhile.Body%2A> pelo menos uma vez, até que uma condição especificada seja avaliada como **falsa**. Se você precisar a atividade contida em um corpo de loop para ser executado zero ou mais vezes, use a atividade de <xref:System.Activities.Statements.While> em vez disso.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriedades DoWhile em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de atividade mais úteis <xref:System.Activities.Statements.DoWhile> e descreve como usá-las no designer:

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Falso|A atividade a ser executada enquanto a condição é **verdadeira**. Para adicionar a <xref:System.Activities.Statements.DoWhile.Body%2A> atividade, remova uma atividade da caixa de ferramentas para o **corpo** de atividade no designer de atividades **DoWhile** com o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Verdadeiro|A condição a ser avaliada após cada iteração do loop. Para definir o <xref:System.Activities.Statements.DoWhile.Condition%2A> , digite uma expressão de Visual Basic na caixa **condição** no designer de atividade **DoWhile** ou na grade de propriedades.|

## <a name="see-also"></a>Confira também

- [While](../workflow-designer/while-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)