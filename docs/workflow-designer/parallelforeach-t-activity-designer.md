---
title: Designer de Fluxo de Trabalho-ParallelForEach &lt;T &gt; designer de atividades
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650084"
---
# <a name="parallelforeach-activity-designer"></a>Designer de atividade do ParallelForEach

A atividade de <xref:System.Activities.Statements.ParallelForEach%601> enumera os elementos de uma coleção e executa uma declaração inserido para cada elemento da coleção paralelamente, que está de forma assíncrona no mesmo segmento. Use esta atividade do controle de fluxo em vez de atividade de <xref:System.Activities.Statements.Sequence> se as atividades filhos desta atividade são esperadas ir ociosa.

A atividade <xref:System.Activities.Statements.ParallelForEach%601> tem uma propriedade <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> que contém uma expressão de Visual Basic especificada pelo usuário. A atividade de <xref:System.Activities.Statements.ParallelForEach%601> avalia essa propriedade após cada ramificação completa. Se for avaliada como **true**, a atividade de <xref:System.Activities.Statements.ParallelForEach%601> será concluída sem executar as outras ramificações. Se a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> não for avaliada como **true**, a atividade de <xref:System.Activities.Statements.ParallelForEach%601> será concluída quando todas as suas atividades filhas forem concluídas.

## <a name="the-parallelforeacht-activity"></a>A atividade ParallelForEach < T \>

<xref:System.Activities.Statements.ParallelForEach%601> enumera os valores e agendamento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera sobre. Agenda somente <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Como o corpo executa depende se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> vai ociosa.

Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> não vai ociosa, executa em uma ordem inversa como as atividades agendados são tratadas como uma pilha, a atividade agendada a última executa primeiro. Por exemplo, se você tiver uma coleção de {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> e usar um **WriteLine** como o corpo para gravar o valor. Você tem 4, 3, 2, 1 impresso no console. Isso ocorre porque o **WriteLine** não fica ocioso, portanto, depois de 4 atividades **WriteLine** terem sido agendadas, elas eram executadas usando um comportamento de pilha (primeiro a fim).

Mas se você tiver atividades em <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pode ir ociosa, como uma atividade de <xref:System.ServiceModel.Activities.Receive> ou a atividade de <xref:System.Activities.Statements.Delay> . Em seguida não há necessidade de esperar que eles terminem concluir. <xref:System.Activities.Statements.ParallelForEach%601> vá para a atividade e tente agendados seguintes corpo de executá-lo. Se a atividade ociosa vai além disso, <xref:System.Activities.Statements.ParallelForEach%601> move novamente em atividade de corpo seguir.

### <a name="using-the-parallelforeacht-activity-designer"></a>Usando o designer de atividade do ParallelForEach \<T >

Acesse o **ParallelForEach \<T >** designer de atividade na categoria **fluxo de controle** da caixa de **ferramentas**.

O designer de atividade do **ParallelForEach \<T >** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que os designers de atividade normalmente são colocados, por exemplo, dentro de uma atividade de **sequência** Designer. Depois de soltá-lo no Designer de Fluxo de Trabalho, ele cria uma atividade <xref:System.Activities.Statements.ParallelForEach%601>, que, por padrão, contém uma <xref:System.Activities.Activity.DisplayName%2A> de **\> ParallelForEach < Int32.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>Propriedades do ParallelForEach < T \> no Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ParallelForEach%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho. O valor padrão é **ParallelForEach \<Int32 >** . O valor pode ser editado opcionalmente na grade de **Propriedades** ou diretamente no cabeçalho do designer de atividade.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|A atividade a executar para cada item na coleção. Para adicionar a atividade de <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, descarte uma atividade da caixa de ferramentas no **corpo** box no **ParallelForEach \<T >** designer de atividade com texto de dica "soltar atividade aqui".|
|**TypeArgument**|verdadeiro|O tipo dos itens na coleção de <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> especificada pelo parâmetro genérico *t*. Por padrão, **TypeArgument** é definido como **Int32**. Para alterar o tipo T no **ParallelForEach < T \>** designer de atividades, altere o valor da caixa de combinação **TypeArgument** na grade de propriedades.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|verdadeiro|A coleção de itens para iterar. Para definir o <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digite uma expressão de Visual Basic na caixa **valores** no designer de atividade **ForEach < t \>** na caixa com o texto de dica "Insira uma expressão vb" ou na caixa **valores** na janela **Propriedades** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Avaliado após cada iteração completa. Se avalia para retificar, então o agendada durante iterações é cancelado. Se esta propriedade não for definida, todas as instruções agendados executam até a conclusão.|

Por padrão, o iterador do loop é chamado item. Você pode alterar o nome da variável de iterador na caixa **foreach** em **ParallelForEach \<T >** designer de atividade. O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ParallelForEach%601> .

## <a name="see-also"></a>Consulte também

- [Sequência](../workflow-designer/sequence-activity-designer.md)
- [Paralelo](../workflow-designer/parallel-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)