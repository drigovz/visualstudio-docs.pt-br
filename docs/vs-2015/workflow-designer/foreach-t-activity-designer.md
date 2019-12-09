---
title: ForEach &lt;T &gt; designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656650"
---
# <a name="foreachlttgt-activity-designer"></a>@No__t_0T ForEach &gt; designer de atividade
A atividade de <xref:System.Activities.Statements.ForEach%601> executa a atividade contida em seu <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada item em uma coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach \<T > Propriedades no Designer de Fluxo de Trabalho
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ForEach%601> e descreve como usá-los no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ForEach%601> . O padrão é ForEach \<Int32 >. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|verdadeiro|A coleção de itens para iterar. Para definir o <xref:System.Activities.Statements.ForEach%601.Values%2A>, digite uma expressão de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] na caixa **valores** na **\<T foreach >** designer de atividade ou na grade de propriedades.|
|*TypeArgument*|verdadeiro|O tipo dos itens na coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada pelo parâmetro genérico *t*. Por padrão, *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor da caixa de combinação *TypeArgument* na grade de propriedades.|

 Por padrão, o iterador de loop é denominado **Item**. Você pode alterar o nome da variável de iterador no designer de atividade de <xref:System.Activities.Statements.ForEach%601> . O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ForEach%601> .

## <a name="see-also"></a>Consulte também
 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [fluxo de controle](../workflow-designer/control-flow-activity-designers.md)