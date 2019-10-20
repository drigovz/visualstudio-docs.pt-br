---
title: Designer de atividade Designer de Fluxo de Trabalho-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 475755fed96f8341c45b8260b414658967b3284c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649747"
---
# <a name="writeline-activity-designer"></a>Designer de atividade WriteLine

O designer de atividade **WriteLine** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>A atividade WriteLine

Grava de atividade de <xref:System.Activities.Statements.WriteLine> texto a <xref:System.IO.TextWriter> um objeto especificado. Se nenhum <xref:System.IO.TextWriter> é especificado, <xref:System.Activities.Statements.WriteLine> grava o texto no console.

### <a name="using-the-writeline-activity-designer"></a>Usando o designer de atividade WriteLine

Acesse o designer de atividade **WriteLine** na categoria **primitivos** da **caixa de ferramentas**. O designer de atividade **WriteLine** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.WriteLine> com <xref:System.Activities.Activity.DisplayName%2A> padrão WriteLine. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **WriteLine** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-writeline-properties"></a>As propriedades WriteLine

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.WriteLine> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas delas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.WriteLine> . O padrão é WriteLine. Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é prática recomendada usar esse.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|O texto a gravação. Para definir a propriedade, digite uma expressão de Visual Basic na caixa de **texto** no designer de atividade **WriteLine** ou na grade de propriedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> a <xref:System.Activities.Statements.WriteLine> que grava <xref:System.Activities.Statements.WriteLine.Text%2A>. O padrão é o console.|

## <a name="see-also"></a>Consulte também

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Atribuir](../workflow-designer/assign-activity-designer.md)
- [Atrasar](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)