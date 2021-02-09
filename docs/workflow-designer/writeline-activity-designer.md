---
title: Designer de atividade Designer de Fluxo de Trabalho-WriteLine
description: Saiba mais sobre a atividade WriteLine e como você pode usar o designer de atividade WriteLine para criar e configurar uma atividade WriteLine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cb4806949b21a6c92548b91623e63306f2a7722
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875101"
---
# <a name="writeline-activity-designer"></a>Designer de atividade WriteLine

O designer de atividade **WriteLine** é usado para criar e configurar uma <xref:System.Activities.Statements.WriteLine> atividade.

## <a name="the-writeline-activity"></a>A atividade WriteLine

Grava de atividade de <xref:System.Activities.Statements.WriteLine> texto a <xref:System.IO.TextWriter> um objeto especificado. Se nenhum <xref:System.IO.TextWriter> é especificado, <xref:System.Activities.Statements.WriteLine> grava o texto no console.

### <a name="using-the-writeline-activity-designer"></a>Usando o designer de atividade WriteLine

Acesse o designer de atividade **WriteLine** na categoria **primitivos** da **caixa de ferramentas**. O designer de atividade **WriteLine** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma atividade de <xref:System.Activities.Statements.WriteLine> com <xref:System.Activities.Activity.DisplayName%2A> padrão WriteLine. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **WriteLine** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-writeline-properties"></a>As propriedades WriteLine

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.WriteLine> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas delas podem ser editadas na superfície Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.WriteLine> . O padrão é WriteLine. Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é prática recomendada usar esse.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Falso|O texto a gravação. Para definir a propriedade, digite uma expressão de Visual Basic na caixa de **texto** no designer de atividade **WriteLine** ou na grade de propriedades.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Falso|<xref:System.IO.TextWriter> a <xref:System.Activities.Statements.WriteLine> que grava <xref:System.Activities.Statements.WriteLine.Text%2A>. O padrão é o console.|

## <a name="see-also"></a>Confira também

- [Primitivos](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Atrasar](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
