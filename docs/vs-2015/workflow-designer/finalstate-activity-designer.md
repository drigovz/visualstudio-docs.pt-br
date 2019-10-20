---
title: Designer de atividade FinalState | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dff9793becc3e0619d42b642609273f328c6aa73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656719"
---
# <a name="finalstate-activity-designer"></a>Designer de atividade de FinalState
O designer de <xref:System.Activities.Core.Presentation.FinalState> é usado para criar <xref:System.Activities.Statements.State> que termina uma instância do computador de estado.

## <a name="using-the-finalstate-activity-designer"></a>Usando o designer de atividade de FinalState
 O designer **FinalState** é usado para criar um <xref:System.Activities.Statements.State> que é pré-configurado como um estado de encerramento em um computador de estado. Um <xref:System.Activities.Statements.State> que é criado usando o designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> tem sua propriedade <xref:System.Activities.Statements.State.IsFinal%2A> definida como **true**, não tem nenhuma atividade de <xref:System.Activities.Statements.State.Exit%2A> e nenhuma transição proveniente dela. Para usar o <xref:System.Activities.Core.Presentation.FinalState> designer de atividade para adicionar uma atividade de <xref:System.Activities.Statements.State> que é pré-configurada como um estado de encerramento em um computador de estado, arraste o designer de atividade **FinalState** da seção **máquina de estado** da **caixa de ferramentas** e solte-o no Designer de fluxo de trabalho. O designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> pode ser solto em <xref:System.Activities.Statements.StateMachine> e as transições adicionados posteriormente; ou uma transição pode ser criada como o designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> é descartada. Para obter mais informações sobre a criação de transições, consulte [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade do estado em Designer de Fluxo de Trabalho
 A tabela a seguir mostra as propriedades que podem ser definidas usando o designer de <xref:System.Activities.Core.Presentation.FinalState> e descreve como elas são usadas no designer. Algumas dessas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.State> no cabeçalho. O valor padrão é **State**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Statements.State.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Statements.State.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Especifica a ação que ocorre quando esse estado é feito a transição para. Esse valor pode ser definido arrastando uma atividade da **caixa de ferramentas** e soltando-a na seção <xref:System.Activities.Statements.State.Entry%2A> do estado.|

## <a name="see-also"></a>Consulte também
 [Transição](../workflow-designer/transition-activity-designer.md) de [estado](../workflow-designer/state-activity-designer.md) [StateMachine](../workflow-designer/statemachine-activity-designer.md)