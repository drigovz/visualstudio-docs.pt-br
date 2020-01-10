---
title: Designer de Fluxo de Trabalho-designer de atividade paralela
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f07dd02f682cd5c61d4d17099c1aeb76bb39bf8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593155"
---
# <a name="parallel-activity-designer"></a>Designer paralelo de atividades

A atividade de <xref:System.Activities.Statements.Parallel> executa uma coleção de filhos atividades simultaneamente.

## <a name="the-parallel-activity"></a>A atividade paralela

A atividade de <xref:System.Activities.Statements.Parallel> armazena as atividades filho em uma coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> . Use a atividade de <xref:System.Activities.Statements.Parallel> em vez de atividade de <xref:System.Activities.Statements.Sequence> se algumas das atividades filho podem ir ociosa.

A atividade <xref:System.Activities.Statements.Parallel> tem uma propriedade <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> que contém uma expressão de Visual Basic especificada pelo usuário. A atividade de <xref:System.Activities.Statements.Parallel> avalia essa propriedade após cada ramificação completa. Se for avaliada como **true**, a atividade de <xref:System.Activities.Statements.Parallel> será concluída sem executar as outras ramificações. Se a <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> não for avaliada como **true**, a atividade de <xref:System.Activities.Statements.Parallel> será concluída quando todas as suas atividades filhas forem concluídas.

### <a name="using-the-parallel-activity-designer"></a>Usando o designer paralelo de atividades

Acesse o designer de atividade **paralela** na categoria **fluxo de controle** da **caixa de ferramentas**.

O designer de atividade **paralela** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde os designers de atividade normalmente são colocados, por exemplo, dentro de um designer de atividade de **sequência** . Depois de soltá-lo no Designer de Fluxo de Trabalho, ele cria uma atividade <xref:System.Activities.Statements.Parallel>, que, por padrão, contém uma <xref:System.Activities.Activity.DisplayName%2A> de **Parallel**

Para adicionar uma atividade à coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> da atividade paralela, arraste outro designer de atividade da caixa de **ferramentas** e solte-o no triângulo dentro do designer de atividade **paralela** . Os triângulos flanqueiam as atividades contidas em ramificações. As atividades adicionais podem ser adicionadas repetindo este procedimento. As atividades podem ser reordenadas arrastando-as e soltando-as no designer de atividade **paralela** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propriedades paralelas de atividade em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades paralelas de atividade e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessário|Medição de|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho. O valor padrão é **Parallel**. O valor pode ser editado opcionalmente na grade de **Propriedades** ou diretamente no cabeçalho do designer de atividade.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|verdadeiro|Contém a coleção de atividades filhos sejam executadas.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Avaliado após uma ramificação completa. Se for avaliado como **true**, os branches pendentes agendados serão cancelados. Se essa propriedade não for definida ou for avaliada como **false**, a atividade será concluída quando todas as suas atividades filhas forem concluídas. O valor padrão é **nulo**.|

## <a name="see-also"></a>Veja também

- [Sequência](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
