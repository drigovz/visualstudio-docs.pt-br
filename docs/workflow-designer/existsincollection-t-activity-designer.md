---
title: Designer de Fluxo de Trabalho-ExistsInCollection &lt;T &gt; designer de atividades
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9dc1f6a3694b6164fe4f2187fa4c6e2b42751e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650483"
---
# <a name="existsincollectiont-activity-designer"></a>Designer de atividade do ExistsInCollection \<T >

O **ExistsInCollection \<T >** designer de atividade é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.ExistsInCollection%601>.

## <a name="the-existsincollectiont-activity"></a>A atividade de > \<T do ExistsInCollection

A atividade de <xref:System.Activities.Statements.ExistsInCollection%601> determina se um item específico existe em uma coleção específico.

### <a name="using-the-existsincollectiont-activity-designer"></a>Usando o designer de atividade do ExistsInCollection \<T >

O **ExistsInCollection \<T >** designer de atividade pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** do designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** +**ALT** +**X**.

O designer de atividade do **ExistsInCollection \<T >** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.ExistsInCollection%601> com uma <xref:System.Activities.Activity.DisplayName%2A> padrão de ExistsInCollection < Int32 \>. (Por padrão, o *TypeArgument* é **Int32**. Ele pode ser alterado na grade de propriedades.)  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade do **ExistsInCollection < t \>** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-existsincollectiont-properties"></a>As propriedades de > \<T ExistsInCollection

A tabela a seguir mostra as propriedades <xref:System.Activities.Statements.ExistsInCollection%601> e descreve como elas são usadas no designer:

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ExistsInCollection%601> . O padrão é ExistsInCollection < Int32 \>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|verdadeiro|O item a ser pesquisado na coleção \<T >. Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|verdadeiro|A coleção na qual verificar se o item existe. Essa coleção é do tipo **ICollection < TypeArgument \>.** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Um valor que indica se o item especificado existe na coleção. Para especificar uma variável para associar ao resultado, digite uma variável do Visual Basic na grade de propriedade.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)