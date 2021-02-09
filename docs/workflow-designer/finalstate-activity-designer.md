---
title: Designer de atividades Designer de Fluxo de Trabalho-FinalState
description: Saiba como você pode usar o designer FinalState para criar um estado que termina uma instância de máquina de estado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a6ec51d17453a13f8c3ab1adffc5447afb5db7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894173"
---
# <a name="finalstate-activity-designer"></a>Designer de atividade de FinalState

O designer de <xref:System.Activities.Core.Presentation.FinalState> é usado para criar <xref:System.Activities.Statements.State> que termina uma instância do computador de estado.

## <a name="using-the-finalstate-activity-designer"></a>Usando o designer de atividade de FinalState

O designer **FinalState** é usado para criar um <xref:System.Activities.Statements.State> que é pré-configurado como um estado de encerramento em um computador de estado. Um <xref:System.Activities.Statements.State> que é criado usando o <xref:System.Activities.Core.Presentation.FinalState> Designer de atividade tem sua <xref:System.Activities.Statements.State.IsFinal%2A> propriedade definida como **true**, não tem <xref:System.Activities.Statements.State.Exit%2A> atividade e nenhuma transição proveniente dela. Para usar o <xref:System.Activities.Core.Presentation.FinalState> Designer de atividade para adicionar uma <xref:System.Activities.Statements.State> atividade que é pré-configurada como um estado de encerramento em um computador de estado, arraste o designer de atividade **FinalState** da seção **máquina de estado** da caixa de **ferramentas** e solte-o no designer de fluxo de trabalho. O designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> pode ser solto em <xref:System.Activities.Statements.StateMachine> e as transições adicionados posteriormente; ou uma transição pode ser criada como o designer de atividade de <xref:System.Activities.Core.Presentation.FinalState> é descartada. Para obter mais informações sobre a criação de transições, consulte [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade do estado em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades que podem ser definidas usando o designer de <xref:System.Activities.Core.Presentation.FinalState> e descreve como elas são usadas no designer. Algumas dessas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.State> no cabeçalho. O valor padrão é **State**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Statements.State.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Statements.State.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Especifica a ação que ocorre quando esse estado é feito a transição para. Esse valor pode ser definido arrastando uma atividade da **caixa de ferramentas** e soltando-a na <xref:System.Activities.Statements.State.Entry%2A> seção do estado.|

## <a name="see-also"></a>Confira também

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
- [Transição](../workflow-designer/transition-activity-designer.md)