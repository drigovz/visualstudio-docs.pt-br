---
title: '&lt;Designer de atividades T &gt; de designer de fluxo de trabalho foreach'
description: Saiba como a <T> atividade ForEach executa a atividade contida em seu corpo para cada item em uma coleção de valores especificada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fd81377ca24dfbeaf4a25f2af00fb69f4821d73
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437977"
---
# <a name="foreachlttgt-activity-designer"></a>&lt;Designer de &gt; atividade ForEach T

A atividade de <xref:System.Activities.Statements.ForEach%601> executa a atividade contida em seu <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada item em uma coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>Propriedades ForEach<T \> no designer de fluxo de trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ForEach%601> e descreve como usá-los no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.ForEach%601> . O padrão é ForEach<Int32 \> . Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Verdadeiro|A coleção de itens para iterar. Para definir o <xref:System.Activities.Statements.ForEach%601.Values%2A> , digite uma expressão de Visual Basic na caixa **valores** no designer de atividade **ForEach \><T** ou na grade de propriedades.|
|*TypeArgument*|Verdadeiro|O tipo dos itens na <xref:System.Activities.Statements.ForEach%601.Values%2A> coleção especificada pelo parâmetro genérico *T*. Por padrão, *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor da caixa de combinação *TypeArgument* na grade de propriedades.|

Por padrão, o iterador de loop é denominado **Item**. Você pode alterar o nome da variável de iterador no designer de atividade de <xref:System.Activities.Statements.ForEach%601> . O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ForEach%601> .

## <a name="see-also"></a>Confira também

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
