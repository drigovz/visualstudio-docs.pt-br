---
title: Designer de fluxo de trabalho - ForEach&lt;T&gt; Designer de atividade
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 838dc50c83147755fb8f0a796ebbac853bba9c14
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999841"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Designer de atividade

A atividade de <xref:System.Activities.Statements.ForEach%601> executa a atividade contida em seu <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada item em uma coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> propriedades em Designer de fluxo de trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ForEach%601> e descreve como usá-los no designer.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ForEach%601> . O padrão é o ForEach < Int32\>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|verdadeiro|A coleção de itens para iterar. Para definir a <xref:System.Activities.Statements.ForEach%601.Values%2A>, digite uma expressão do Visual Basic na **valores** caixa no **ForEach < T\>**  atividade designer ou na grade de propriedade.|
|*TypeArgument*|verdadeiro|O tipo dos itens na <xref:System.Activities.Statements.ForEach%601.Values%2A> coleção especificada pelo parâmetro genérico *T*. Por padrão, *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor da *TypeArgument* caixa de combinação na grade de propriedade.|

Por padrão, o iterador do loop é denominado **item**. Você pode alterar o nome da variável de iterador no designer de atividade de <xref:System.Activities.Statements.ForEach%601> . O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ForEach%601> .

## <a name="see-also"></a>Consulte também

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)