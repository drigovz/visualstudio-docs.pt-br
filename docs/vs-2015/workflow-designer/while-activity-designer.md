---
title: Embora o designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606616"
---
# <a name="while-activity-designer"></a>Quando designer de atividades

A <xref:System.Activities.Statements.While> atividade executa a atividade contida em seu <xref:System.Activities.Statements.While.Body%2A> enquanto a condição especificada é avaliada como **true**. A atividade contida nunca pode executar. Se você desejar que a atividade contida a ser executada pelo menos uma vez, use a atividade de <xref:System.Activities.Statements.DoWhile> em vez disso.

## <a name="while-properties-in-workflow-designer"></a>Quando propriedades em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.While> e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.While> no cabeçalho. O valor padrão é quando. O valor pode ser editado na janela **Propriedades** ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.While.Body%2A>|Falso|Contém a atividade a ser executada enquanto o <xref:System.Activities.Statements.While.Condition%2A> é avaliado como **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Verdadeiro|Contém a expressão de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] que é avaliada para determinar se a atividade em <xref:System.Activities.Statements.While.Body%2A> deve ser executada.|

## <a name="see-also"></a>Confira também

- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)