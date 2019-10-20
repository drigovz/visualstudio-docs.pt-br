---
title: Designer de atividade Designer de Fluxo de Trabalho-FlowDecision
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2274333de9255ff818b4ee6952bfa1b2a99c59b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650436"
---
# <a name="flowdecision-activity-designer"></a>Designer de atividade de FlowDecision

O nó de <xref:System.Activities.Statements.FlowDecision> é um nó condicional que fornece uma ramificação para o fluxo de controle em uma das duas alternativas com base em se uma condição especificada é satisfeita. Se o fluxo requer mais de duas ramificações, use <xref:System.Activities.Statements.FlowSwitch%601> em vez disso.

## <a name="the-flowdecision-node"></a>O nó de FlowDecision

Use <xref:System.Activities.Statements.FlowDecision> quando o fluxo pode ser transformada em dois caminhos. Um nó de <xref:System.Activities.Statements.FlowDecision> tem <xref:System.Activities.Statements.FlowDecision.Condition%2A> e <xref:System.Activities.Statements.FlowNode> associados a cada um dos dois resultados possíveis: <xref:System.Activities.Statements.FlowDecision.True%2A> ou <xref:System.Activities.Statements.FlowDecision.False%2A>. <xref:System.Activities.Statements.FlowDecision.Condition%2A> é avaliado e o valor da avaliação determina <xref:System.Activities.Statements.FlowNode> a seguir seja processado dentro de <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilizando o designer de FlowDecision

O **FlowDecision** designer pode ser encontrado na categoria **fluxograma** da caixa de **ferramentas**, que é acessada clicando na guia **caixa de ferramentas** na Designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** +**ALT** +**X**.

O designer de **FlowDecision** pode ser arrastado da **caixa de ferramentas** e retirado para a superfície de designer de fluxo de trabalho dentro de um designer de atividade de **fluxograma** . Isso cria um <xref:System.Activities.Statements.FlowDecision> rotulado como **decisão** dentro da atividade de <xref:System.Activities.Statements.Flowchart>. O mouse sobre o designer e os identificadores quadrados **verdadeiro** e **falso** para as duas ramificações são exibidos.

Depois de arrastar o designer de **FlowDecision** e outros designers para o **fluxograma**, os nós podem ser vinculados juntos para especificar a ordem de execução. Para criar um link entre um nó de origem (incluindo as ramificações **true** e **false** do **FlowDecision**) e um nó de destino, o mouse sobre o designer do nó de origem e os identificadores quadrados aparecem em cada lado dele. Clique em uma das alças de quadradas e arraste-a segurando o botão do mouse na uma das alças que aparece de maneira similar ao redor do nó de destino quando você o mouse sobre ele. Liberar o botão do mouse e um link é criado no meio esses dois nós que é representado como uma seta do designer de origem para o designer de destino.

A expressão que declara a <xref:System.Activities.Statements.FlowDecision.Condition%2A> pode ser digitada na caixa **condição** da janela **Propriedades** clicando em onde o texto de dica diz "inserir uma expressão vb".

### <a name="the-flowdecision-properties"></a>As propriedades de FlowDecision

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.FlowDecision> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|verdadeiro|A condição que determina que caminho o controle de fluxo leva.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|O caminho tomada pelo controle de fluxo se <xref:System.Activities.Statements.FlowDecision.Condition%2A> estiver satisfeito.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|O caminho tomada pelo controle de fluxo se <xref:System.Activities.Statements.FlowDecision.Condition%2A> não estiver satisfeito.|

## <a name="see-also"></a>Consulte também

- [Fluxograma](../workflow-designer/flowchart-activity-designers.md)
- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)