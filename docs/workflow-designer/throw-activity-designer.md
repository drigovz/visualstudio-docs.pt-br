---
title: Designer de atividade Designer de Fluxo de Trabalho-throw
description: Saiba mais sobre a atividade Throw e como você pode usar o designer de atividade Throw para criar e configurar uma atividade Throw.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d836a666c0b09366f5c8f3c9245def63faba462
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433850"
---
# <a name="throw-activity-designer"></a>Lance o designer de atividades

O designer de atividade de **geração** é usado para criar e configurar uma <xref:System.Activities.Statements.Throw> atividade.

## <a name="the-throw-activity"></a>A atividade throw

A atividade de <xref:System.Activities.Statements.Throw> gerencie uma exceção.

### <a name="using-the-throw-activity-designer"></a>Usando o designer de atividade throw

Acesse o designer de atividade de **geração** na categoria **tratamento de erros** da **caixa de ferramentas**.

O designer de atividade de **throw** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.Throw> atividade com um **DisplayName** padrão de Throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade de **geração** ou na caixa **DisplayName** da grade de propriedades. A propriedade de <xref:System.Activities.Statements.Throw.Exception%2A> deve ser editada na grade de propriedade.

### <a name="the-throw-properties"></a>As propriedades throw

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Throw> e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Throw> . O padrão é throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|Verdadeiro|A exceção para lançar. Esta exceção deve derivar de <xref:System.Exception>. Para especificar a exceção, digite uma expressão do Visual Basic na grade de propriedade.|

## <a name="see-also"></a>Confira também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [Relançar](../workflow-designer/rethrow-activity-designer.md)
- [Designer de atividade Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
