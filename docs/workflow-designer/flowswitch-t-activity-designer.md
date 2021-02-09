---
title: Designer de atividades Designer de Fluxo de Trabalho-FlowSwitch &lt; T &gt;
description: Saiba como a <T> atividade FlowSwitch é um nó condicional que fornece ramificações para o fluxo de controle com base no critério de correspondência.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f61dd3f14ba527e9f5be0e009825902e683fb1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876557"
---
# <a name="flowswitcht-activity-designer"></a>Designer de atividade FlowSwitch\<T>

A atividade de <xref:System.Activities.Statements.FlowSwitch%601> é um nó condicional que fornece a ramificação para o fluxo de controle baseado no critério de correspondência quando mais de duas ramificações alternativas são necessários. Se a ramificação de fluxo requer apenas dois caminhos, use a atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.

## <a name="the-flowswitcht-activity"></a>A \<T> atividade FlowSwitch

A <xref:System.Activities.Statements.FlowSwitch%601> atividade contém um <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que retorna um valor do tipo *T* (especificado pelo parâmetro genérico) quando avaliado. A atividade também contém um conjunto de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica um mapeamento exclusivo de resultados possíveis da avaliação a um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> . O <xref:System.Activities.Statements.FlowNode> executado é aquele cujo objeto do tipo *T* corresponde ao valor de avaliado <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Os exemplos de <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> podem opcionalmente () são fornecidos para casos em que nenhuma correspondência for obtida.

### <a name="using-the-flowswitcht-activity-designer"></a>Usando o \<T> Designer de atividade FlowSwitch

O designer de atividade do **FlowSwitch \<T>** pode ser encontrado na categoria **fluxograma** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** no lado esquerdo da designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

O designer de atividade do **FlowSwitch \<T>** pode ser arrastado da **caixa de ferramentas** e retirado para a superfície de designer de fluxo de trabalho dentro de um designer de atividade de **fluxograma** . Use a janela **Selecionar tipos** que é exibida para especificar o tipo (associado ao código com o <xref:System.Activities.Statements.FlowSwitch%601> parâmetro de seu genérico) obtido da avaliação do <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Este procedimento cria uma <xref:System.Activities.Statements.FlowSwitch%601> atividade rotulada como **opção** na <xref:System.Activities.Statements.Flowchart> atividade. O <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> pode ser digitado na caixa **expressão** da janela **Propriedades** clicando em onde o texto de dica diz "inserir uma expressão vb".

Passe o mouse sobre o designer de atividade **FlowSwitch \<T>** para fazer com que as alças quadradas que são usadas para vincular-se apareçam ao longo de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> suas bordas. Depois de arrastar o **FlowSwitch<\> T** Activity Designer e outros designers de atividade para o **fluxograma**, os <xref:System.Activities.Activity> objetos que eles representam estarão prontos para serem vinculados para especificar a ordem de execução. Para criar um dos <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associados com <xref:System.Activities.Statements.FlowSwitch%601> , clique em um dos identificadores de caso quadrado no perímetro do **FlowSwitch<T \>** e arraste-o (segurando o botão do mouse) para um dos identificadores que aparece de maneira semelhante em relação à atividade de destino quando o mouse passa sobre seu designer. Solte o botão do mouse e uma seta do **FlowSwitch<T \>** ao designer de destino aparecerá representando esse caso. O valor padrão para esse caso é exibido na seta e pode ser editado na caixa de **caso** da janela **Propriedades** .

### <a name="the-flowswitcht-properties"></a>As \<T> Propriedades FlowSwitch

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.FlowSwitch%601> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica a expressão que é avaliada para determinar qual de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> para alternar o caminho execução.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|Falso|Especifica um mapeamento exclusivo de resultados possíveis obtidos de avaliar <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> a um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> .|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especificar o mapeamento quando a avaliação de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> não coincide com um dos valores contidos no objeto de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|

## <a name="see-also"></a>Confira também

- [Fluxograma](../workflow-designer/flowchart-activity-designers.md)
- [Fluxograma](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
