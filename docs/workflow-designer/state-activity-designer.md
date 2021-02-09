---
title: Designer de atividade de Designer de Fluxo de Trabalho estado
description: Saiba mais sobre a atividade StateMachine e como você pode usar o designer de atividade de estado para adicionar um estado a um fluxo de trabalho.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: abf4e81ecd258668c93b674410f029e6be0f5bf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873509"
---
# <a name="state-activity-designer"></a>Designer de atividade de estado

<xref:System.Activities.Statements.State> representa um estado em que um computador de estado pode estar.

## <a name="using-the-state-activity-designer"></a>Usando o designer de atividade de estado

Para adicionar um <xref:System.Activities.Statements.State> a um fluxo de trabalho, arraste o designer de atividade de **estado** da seção **máquina de estado** da caixa de **ferramentas** e solte-o em uma <xref:System.Activities.Statements.StateMachine> atividade na superfície de designer de fluxo de trabalho. Uma atividade de <xref:System.Activities.Statements.State> pode ser arrastada em <xref:System.Activities.Statements.StateMachine> e as transições adicionados posteriormente; ou uma transição pode ser criada como a atividade de <xref:System.Activities.Statements.State> é descartada. Para adicionar uma <xref:System.Activities.Statements.State> atividade e criar uma transição em uma etapa, arraste uma atividade de **estado** da seção **máquina de estado** da **caixa de ferramentas** e passe o mouse sobre outro Estado no designer de fluxo de trabalho. Quando <xref:System.Activities.Statements.State> arrastado está sobre um outro <xref:System.Activities.Statements.State>, quatro triângulos aparecerão em torno do outro <xref:System.Activities.Statements.State>. Se <xref:System.Activities.Statements.State> é solto em um dos quatro triângulos, é adicionado ao computador de estado e uma transição é criada de origem <xref:System.Activities.Statements.State> ao destino solto <xref:System.Activities.Statements.State>. Para obter mais informações, consulte [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriedades de atividade do estado em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.State> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer. Algumas dessas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.State> no cabeçalho. O valor padrão é **State**. O valor pode ser editado na grade de propriedade ou diretamente no cabeçalho do designer de atividade. <xref:System.Activities.Statements.State.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Statements.State.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.State.Entry%2A>|Falso|Especifica a ação que ocorre quando esse estado é feito a transição para. Quando a <xref:System.Activities.Statements.State> atividade é expandida, esse valor pode ser definido arrastando-se uma atividade da **caixa de ferramentas** e soltando-a na seção de **entrada** do estado.|
|<xref:System.Activities.Statements.State.Exit%2A>|Falso|Especifica a ação que ocorre quando esse estado é feito a transição fora. Quando a <xref:System.Activities.Statements.State> atividade é expandida, esse valor pode ser definido arrastando-se uma atividade da **caixa de ferramentas** e soltando-a na seção de **saída** do estado.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Falso|Lista as transições possíveis que originam de <xref:System.Activities.Statements.State>. Cada item na lista possui um link a <xref:System.Activities.Statements.Transition> associado e de destino <xref:System.Activities.Statements.State>. Clicar no link alternará o designer para uma exibição expandida de <xref:System.Activities.Statements.Transition> ou de <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Consulte também

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transição](../workflow-designer/transition-activity-designer.md)
