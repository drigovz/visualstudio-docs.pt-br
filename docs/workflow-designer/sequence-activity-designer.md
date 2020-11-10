---
title: Designer de atividade de Designer de Fluxo de Trabalho sequência
description: Saiba como a atividade Sequence contém uma coleção ordenada de atividades filho que ela executa na ordem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9e7e6e9114405bc1575e0256dd63211a4fb6d08
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433967"
---
# <a name="sequence-activity-designer"></a>Arranje seqüencialmente o designer de atividades

A atividade de <xref:System.Activities.Statements.Sequence> contém uma coleção ordenada de atividades filhos que executa em ordem.

Outra maneira de executar um conjunto de atividades em ordem é usar uma atividade de <xref:System.Activities.Statements.Flowchart> . Considere usar o [fluxograma](../workflow-designer/flowchart-activity-designer.md) quando você tiver um fluxo de programa de ramificação simples ou de looping que você deseja modelar diagramaticamente.

## <a name="using-the-sequence-activity-designer"></a>Usando o designer de atividade de sequência

Para adicionar uma <xref:System.Activities.Statements.Sequence> atividade, arraste o designer de atividade de **sequência** da **caixa de ferramentas** e solte-o na superfície de designer de fluxo de trabalho. Para adicionar uma atividade filho a essa <xref:System.Activities.Statements.Sequence> atividade, arraste alguma outra atividade da caixa de **ferramentas** e solte-a no triângulo, no box, com o texto de dica "soltar atividade aqui".

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade da sequência em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Sequence> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Sequence> no cabeçalho. O valor padrão é sequência. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Confira também

- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)