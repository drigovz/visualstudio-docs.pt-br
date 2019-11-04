---
title: StateMachine designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660112"
---
# <a name="statemachine-activity-designer"></a>Designer de atividade de StateMachine
A atividade de <xref:System.Activities.Statements.StateMachine> contém uma coleção de estados e modelos de fluxos de trabalho usando o paradigma familiar do computador de estado.

## <a name="using-the-statemachine-activity-designer"></a>Usando o designer de atividade de StateMachine
 Para adicionar uma atividade de <xref:System.Activities.Statements.StateMachine>, arraste o designer de atividade **StateMachine** da seção **máquina de estado** da **caixa de ferramentas** e solte-o na superfície [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Para adicionar um estado filho a essa atividade de <xref:System.Activities.Statements.StateMachine>, arraste uma <xref:System.Activities.Statements.State> ou <xref:System.Activities.Core.Presentation.FinalState> da **caixa de ferramentas** e solte-a na **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade de StateMachine em Designer de Fluxo de Trabalho
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.StateMachine> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.StateMachine> no cabeçalho. O valor padrão é **StateMachine**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Activity.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|

## <a name="see-also"></a>Consulte também
 [Fluxo de controle](../workflow-designer/control-flow-activity-designers.md) [de fluxograma](../workflow-designer/flowchart-activity-designer.md)