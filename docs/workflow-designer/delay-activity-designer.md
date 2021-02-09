---
title: Designer de atividade de Designer de Fluxo de Trabalho atraso
description: Saiba mais sobre as atividades de atraso e como você pode usar o designer de atividade de atraso para criar e configurar uma atividade de atraso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1b661dddf6c07bca34e5ea044fd1338da68f4e19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894303"
---
# <a name="delay-activity-designer"></a>Atrasar o designer de atividades

O designer de atividade de **atraso** é usado para criar e configurar uma <xref:System.Activities.Statements.Delay> atividade.

## <a name="the-delay-activity"></a>A atividade de atraso

A atividade de <xref:System.Activities.Statements.Delay> atrasa a execução de um fluxo de trabalho para uma quantidade de tempo especificada.

### <a name="use-the-delay-activity-designer"></a>Usar o designer de atividade de atraso

O designer de atividade de **atraso** pode ser encontrado na categoria **primitivos** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** do designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

O designer de atividade de **atraso** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade cria uma <xref:System.Activities.Statements.Delay> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de atraso. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **atraso** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-delay-properties"></a>As propriedades de atraso

A tabela a seguir mostra as <xref:System.Activities.Statements.Delay> Propriedades e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades e algumas delas podem ser editadas na superfície de Designer de Fluxo de Trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.Delay> . O padrão é atraso. Embora o <xref:System.Activities.Activity.DisplayName%2A> valor não seja estritamente necessário, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|A quantidade de tempo para atrasar o fluxo de trabalho. Essa propriedade é definida na grade de propriedade. Digite qualquer um <xref:System.TimeSpan> literal no 00:00 de formato: 00 ou uma expressão do Visual Basic para especificar a quantidade de tempo.|

## <a name="see-also"></a>Confira também

- [Primitivos](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Atrasar o designer de atividades](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)