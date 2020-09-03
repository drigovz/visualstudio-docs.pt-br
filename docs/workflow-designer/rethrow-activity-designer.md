---
title: Designer de Fluxo de Trabalho-relançar o designer de atividade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cb73a674e702d54f970c5dea7ec051f100382c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114756"
---
# <a name="rethrow-activity-designer"></a>Designer de atividade de Relançar

O designer de atividade **Rethrow** é usado para criar e configurar uma <xref:System.Activities.Statements.Rethrow> atividade.

## <a name="the-rethrow-activity"></a>A atividade Rethrow

A atividade de <xref:System.Activities.Statements.Rethrow> lança uma exceção lançada anteriormente. Esta atividade somente pode ser usada em um manipulador de <xref:System.Activities.Statements.Catch> na atividade de <xref:System.Activities.Statements.TryCatch> .

### <a name="use-the-rethrow-activity-designer"></a>Usar o designer de atividade Rethrow

Acesse o designer de atividade **Rethrow** na categoria **tratamento de erros** da **caixa de ferramentas**. O designer de atividade **Rethrow** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade cria uma <xref:System.Activities.Statements.Rethrow> atividade com um **DisplayName** padrão de Throw. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade **Rethrow** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-rethrow-properties"></a>As propriedades Rethrow

A tabela a seguir mostra as <xref:System.Activities.Statements.Rethrow> Propriedades e descreve como elas são usadas no designer:

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Rethrow> . O padrão é Relançar.|

## <a name="see-also"></a>Confira também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
