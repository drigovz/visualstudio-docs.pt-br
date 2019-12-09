---
title: Atribuir designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659187"
---
# <a name="assign-activity-designer"></a>Atribua o designer de atividades
O designer de atividade de **atribuição** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Assign>.

## <a name="the-assign-activity"></a>A atividade atribuir
 A atividade de <xref:System.Activities.Statements.Assign> atribui um valor a uma variável ou um argumento.

### <a name="using-the-assign-activity-designer"></a>Usando o designer de atividade atribuir
 O designer de atividade de **atribuição** pode ser encontrado na categoria **primitivos** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** (como alternativa, selecione caixa de **ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade de **atribuição** pode ser arrastado da **caixa de ferramentas** e colocado na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)], onde as atividades sempre são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.Assign> com um **DisplayName** padrão de assign. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **atribuição** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-assign-properties"></a>As propriedades atribuir
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Assign> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e algumas delass podem ser editadas na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.Assign> . O padrão é atribui. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Assign.To%2A>|verdadeiro|A variável ou o argumento para que <xref:System.Activities.Statements.Assign.Value%2A> é atribuído. Isso deve ser um identificador válido Visual Basic. Para definir a propriedade, digite uma expressão de Visual Basic na caixa **para** no designer de atividade de **atribuição** ou na grade de propriedades.|
|<xref:System.Activities.Statements.Assign.Value%2A>|verdadeiro|O valor que é atribuído à variável. Para definir o <xref:System.Activities.Statements.Assign.Value%2A>, digite uma expressão de Visual Basic na caixa **valor** no designer de atividade **atribuir** ou na grade de propriedades.|

## <a name="see-also"></a>Consulte também
 [Primitivos](../workflow-designer/primitives-activity-designers.md) [atrasam](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)