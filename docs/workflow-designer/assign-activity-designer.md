---
title: Designer de Fluxo de Trabalho-atribuir designer de atividade
description: Saiba como você pode usar o designer de atividade assign para criar e configurar uma atividade atribuir e como a atividade atribuir atribui um valor a uma variável ou argumento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d8601951cfaba3f246e8488ab23c9b6ccad0d01
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438185"
---
# <a name="assign-activity-designer"></a>Atribua o designer de atividades

O designer de atividade de **atribuição** é usado para criar e configurar uma <xref:System.Activities.Statements.Assign> atividade.

## <a name="the-assign-activity"></a>A atividade atribuir

A atividade de <xref:System.Activities.Statements.Assign> atribui um valor a uma variável ou um argumento.

### <a name="using-the-assign-activity-designer"></a>Usando o designer de atividade atribuir

O designer de atividade de **atribuição** pode ser encontrado na categoria **primitivos** da **caixa de ferramentas** , que é acessada clicando na guia **caixa de ferramentas** (como alternativa, selecione caixa de **ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

O designer de atividade de **atribuição** pode ser arrastado da **caixa de ferramentas** e retirado para a superfície de designer de fluxo de trabalho onde as atividades sempre são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade de **atribuição** cria uma <xref:System.Activities.Statements.Assign> atividade com um **DisplayName** padrão de atribuir. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **assign** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-assign-properties"></a>As propriedades atribuir

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Assign> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas delas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.Assign> . O padrão é atribui. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Assign.To%2A>|Verdadeiro|A variável ou o argumento para que <xref:System.Activities.Statements.Assign.Value%2A> é atribuído. O valor deve ser um identificador de Visual Basic válido. Para definir a propriedade, digite uma expressão de Visual Basic na caixa **para** no designer de atividade de **atribuição** ou na grade de propriedades.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Verdadeiro|O valor que é atribuído à variável. Para definir o <xref:System.Activities.Statements.Assign.Value%2A> , digite uma expressão de Visual Basic na caixa **valor** no designer de atividade **atribuir** ou na grade de propriedades.|

## <a name="see-also"></a>Confira também

- [Primitivos](../workflow-designer/primitives-activity-designers.md)
- [Atrasar](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)