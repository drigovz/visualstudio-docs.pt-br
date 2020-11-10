---
title: Designer de Fluxo de Trabalho-designer de atividade paralela
description: Saiba mais sobre a atividade paralela e como usar o designer de atividade paralela para executar uma coleção de atividades filho simultaneamente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8751c15e40658e7a901550eef3d86050da842cc7
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435593"
---
# <a name="parallel-activity-designer"></a>Designer paralelo de atividades

A atividade de <xref:System.Activities.Statements.Parallel> executa uma coleção de filhos atividades simultaneamente.

## <a name="the-parallel-activity"></a>A atividade paralela

A atividade de <xref:System.Activities.Statements.Parallel> armazena as atividades filho em uma coleção de <xref:System.Activities.Statements.Parallel.Branches%2A> . Use a atividade de <xref:System.Activities.Statements.Parallel> em vez de atividade de <xref:System.Activities.Statements.Sequence> se algumas das atividades filho podem ir ociosa.

A <xref:System.Activities.Statements.Parallel> atividade tem uma <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> propriedade que contém uma expressão de Visual Basic especificada pelo usuário. A atividade de <xref:System.Activities.Statements.Parallel> avalia essa propriedade após cada ramificação completa. Se for avaliada como **true** , a <xref:System.Activities.Statements.Parallel> atividade será concluída sem executar as outras ramificações. Se o <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> não for avaliado como **true** , a <xref:System.Activities.Statements.Parallel> atividade será concluída quando todas as suas atividades filhas forem concluídas.

### <a name="using-the-parallel-activity-designer"></a>Usando o designer paralelo de atividades

Acesse o designer de atividade **paralela** na categoria **fluxo de controle** da **caixa de ferramentas**.

O designer de atividade **paralela** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde os designers de atividade normalmente são colocados, por exemplo, dentro de um designer de atividade de **sequência** . Depois de soltá-lo no Designer de Fluxo de Trabalho, ele cria uma <xref:System.Activities.Statements.Parallel> atividade, que por padrão contém um <xref:System.Activities.Activity.DisplayName%2A> de **Parallel**

Para adicionar uma atividade à <xref:System.Activities.Statements.Parallel.Branches%2A> coleção da atividade Parallel, arraste outro designer de atividades da **caixa de ferramentas** e solte-o no triângulo dentro do **Parallel** Activity Designer. Os triângulos flanqueiam as atividades contidas em ramificações. As atividades adicionais podem ser adicionadas repetindo este procedimento. As atividades podem ser reordenadas arrastando-as e soltando-as no designer de atividade **paralela** .

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Propriedades paralelas de atividade em Designer de Fluxo de Trabalho

A tabela a seguir mostra as propriedades paralelas de atividade e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável para exibição do designer de atividade no cabeçalho. O valor padrão é **Parallel**. O valor pode ser editado opcionalmente na grade de **Propriedades** ou diretamente no cabeçalho do designer de atividade.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Verdadeiro|Contém a coleção de atividades filhos sejam executadas.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Falso|Avaliado após uma ramificação completa. Se for avaliado como **true** , os branches pendentes agendados serão cancelados. Se essa propriedade não for definida ou for avaliada como **false** , a atividade será concluída quando todas as suas atividades filhas forem concluídas. O valor padrão é **NULL**.|

## <a name="see-also"></a>Confira também

- [Sequência](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
