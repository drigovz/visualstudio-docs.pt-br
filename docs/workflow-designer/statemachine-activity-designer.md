---
title: Designer de atividade Designer de Fluxo de Trabalho-StateMachine
description: Saiba como a atividade StateMachine contém uma coleção de Estados e fluxos de trabalho de modelos usando o paradigma de máquina de estado familiar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: dacb6dfa5c30ce174c64accfedf82f1c288c734d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433941"
---
# <a name="statemachine-activity-designer"></a>Designer de atividade de StateMachine

A atividade de <xref:System.Activities.Statements.StateMachine> contém uma coleção de estados e modelos de fluxos de trabalho usando o paradigma familiar do computador de estado.

## <a name="using-the-statemachine-activity-designer"></a>Usando o designer de atividade de StateMachine

Para adicionar uma <xref:System.Activities.Statements.StateMachine> atividade, arraste o designer de atividade **StateMachine** da seção **máquina de estado** da **caixa de ferramentas** e solte-o na superfície de designer de fluxo de trabalho. Para adicionar um estado filho a essa <xref:System.Activities.Statements.StateMachine> atividade, arraste uma <xref:System.Activities.Statements.State> ou <xref:System.Activities.Core.Presentation.FinalState> da **caixa de ferramentas** e solte-a na **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade de StateMachine em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.StateMachine> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.StateMachine> no cabeçalho. O valor padrão é **StateMachine**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Activity.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Confira também

- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
