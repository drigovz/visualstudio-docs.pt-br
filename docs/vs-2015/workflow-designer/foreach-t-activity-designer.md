---
title: ForEach&lt;T&gt; Designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 97732b92c5a90334917ad4e74667f88d605b647d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943284"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; Designer de atividade
A atividade de <xref:System.Activities.Statements.ForEach%601> executa a atividade contida em seu <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada item em uma coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach\<T > propriedades em Designer de fluxo de trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ForEach%601> e descreve como usá-los no designer.  
  
|Nome da Propriedade|Necessária|Uso|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ForEach%601> . O padrão é o ForEach\<Int32 >. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|verdadeiro|A coleção de itens para iterar. Para definir a <xref:System.Activities.Statements.ForEach%601.Values%2A>, digite um [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expressão na **valores** caixa no **ForEach\<T >** atividade designer ou na grade de propriedade.|  
|*TypeArgument*|verdadeiro|O tipo dos itens na <xref:System.Activities.Statements.ForEach%601.Values%2A> coleção especificada pelo parâmetro genérico *T*. Por padrão, *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor da *TypeArgument* caixa de combinação na grade de propriedade.|  
  
 Por padrão, o iterador do loop é denominado **item**. Você pode alterar o nome da variável de iterador no designer de atividade de <xref:System.Activities.Statements.ForEach%601> . O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ForEach%601> .  
  
## <a name="see-also"></a>Consulte também  
 [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)