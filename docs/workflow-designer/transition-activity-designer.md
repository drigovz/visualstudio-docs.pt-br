---
title: Designer de atividade de transição de Designer de Fluxo de Trabalho
description: Saiba como você pode usar o designer de atividade de transição para configurar uma transição entre dois Estados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 24a20ca9f7905adee3b7d0d83801d0033a1752ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875270"
---
# <a name="transition-activity-designer"></a>Fazer a transição o designer de atividades

<xref:System.Activities.Statements.Transition> representa a transição entre dois estados.

## <a name="using-the-transition-activity-designer"></a>Usando o designer de atividade de transição

O designer de atividade de transição permite que você configure uma transição entre dois estados.

### <a name="transition-properties-in-the-workflow-designer"></a>Propriedades de transição em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Transition> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Transition> . O valor padrão é **T1**. O valor pode ser editado na grade de propriedade, no cabeçalho de designer expandido de transição, e o cabeçalho da seção de ação dentro do designer expandido de transição. <xref:System.Activities.Activity.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|Falso|Se presente, especifica uma expressão que deve ser avaliada como **verdadeira** antes de o controle ser passado para o estado de destino. Essa condição pode ser editada na grade de propriedade e expandido no designer de transição. Várias condições em uma transição compartilhado são avaliadas na ordem em que aparecem no designer de transição. **Observação:**  Observe que, se a <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como **false** (ou se todas as condições de uma transição de gatilho compartilhado forem avaliadas como **false**), a transição não ocorrerá e todos os gatilhos de todas as transições do estado serão reagendados. Neste tutorial, essa situação não pode ocorrer devido à maneira como as condições são configuradas (temos ações específicas para se o palpite está correto ou incorreto).|
|**Origem**|True|Indica o estado de que essa transição se origina. Clicando no nome do estado de origem alterna a exibição do designer para uma exibição expandida de estado. Esse valor é definido quando a transição é criada e não pode ser alterada.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|Falso|Especifica a atividade cuja conclusão inicia a transição. Para definir essa atividade, arraste uma atividade da **caixa de ferramentas** e solte-a na seção **gatilho** da transição.|
|<xref:System.Activities.Statements.Transition.Action%2A>|Falso|Especifica a atividade que é executada quando a atividade de gatilho é concluída e o <xref:System.Activities.Statements.Transition.Condition%2A> , se presente, é avaliado como **verdadeiro**. Esta atividade é executada ao fazer a transição para estado de destino, após a atividade de <xref:System.Activities.Statements.State.Exit%2A> para o estado de origem, se presentes, é executada. Quando o designer de transição é expandido, esse valor pode ser definido arrastando uma atividade da **caixa de ferramentas** e soltando-o na seção de **ação** da transição. Pode haver várias ações para uma única transição. As ações individuais podem ser expandidos e reduzido, e podem ser classificadas clicando para cima ou para baixo a seta que aparece em ação quando há várias ações em uma transição.|
|**Destino**|True|Indica o estado que as transições do computador de estado após a transição concluírem. Isso corresponde à propriedade de <xref:System.Activities.Statements.Transition.To%2A> de transição no modelo de objeto. Clicando no nome do estado de destino alterna a exibição do designer para uma exibição expandida de estado. Esse valor é definido quando a transição é criada e pode ser modificada arrastando a seta que se conecta a transição para estado de destino no designer.|

### <a name="creating-transitions"></a>Criar transições

As transições são criados arrastando uma linha de um estado para outro, ou soltando um estado em triângulos que aparecem quando um estado é arrastado sobre outro estado. Para criar uma transição, arrastando passa o mouse sobre a borda do estado de origem, e arraste uma linha de estado da fonte para o estado de destino. Para criar uma transição soltando-se, arraste o estado de destino e focalizar-lo sobre o estado de origem, e solte-o em um dos quatro triângulos que aparecem em torno do estado de exibição source. O estado de destino pode ser um novo estado arrastado da **caixa de ferramentas** ou um estado existente arrastado do designer de fluxo de trabalho.

> [!NOTE]
> Um único estado em um computador de estado pode ter até 76 transições criadas utilizando o designer de fluxo de trabalho. O limite nas transições para um estado para fluxos de trabalho criados fora de designer é delimitado somente por recursos do sistema.

As transições compartilhadas do disparador são o conjunto de transições que compartilham o mesmo evento do disparador. Um disparador compartilhado permite a progressão condicional a um estado de destino com base na classificação de expressões configuradas para várias transições que compartilham um evento comuns de disparador. Para adicionar ações adicionais para uma transição e criar uma transição compartilhada, clique no círculo que indica o início de transição desejada e arraste-o para estado desejado. A nova transição compartilhar um disparador mesmo que a transição inicial, mas terá uma condição e uma ação exclusivos. As transições compartilhadas também podem ser criadas de dentro do designer de transição clicando em **Adicionar transição de gatilho compartilhado** na parte inferior do designer de transição e, em seguida, selecionando o estado de destino desejado na lista suspensa **Estados disponíveis para conexão** .

## <a name="see-also"></a>Consulte também

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [State](../workflow-designer/state-activity-designer.md)
