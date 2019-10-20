---
title: Designer de Fluxo de Trabalho-RemoveFromCollection &lt;T &gt; designer de atividades
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8885505607d654327ad9dc36ab88708ab708c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649997"
---
# <a name="removefromcollectiont-activity-designer"></a>Designer de atividade do RemoveFromCollection \<T >

O **RemoveFromCollection \<T >** designer de atividade é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiontactivity"></a>A atividade de > \<T do RemoveFromCollection

A atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> remover um item específico de uma coleção específico.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usando o designer de atividade do RemoveFromCollection \<T >

Acesse o **RemoveFromCollection \<T >** designer de atividade na categoria **coleção** da **caixa de ferramentas**.
O designer de atividade do **RemoveFromCollection \<T >** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> com uma <xref:System.Activities.Activity.DisplayName%2A> padrão de RemoveFromCollection < Int32 \>. O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade do **RemoveFromCollection < t \>** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-removefromcollectiont-properties"></a>As Propriedades RemoveFromCollection < T \>

A tabela a seguir mostra as propriedades <xref:System.Activities.Statements.RemoveFromCollection%601> e descreve como elas são usadas no designer:

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> . O padrão é o RemoveFromCollection < Int32 \>.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|verdadeiro|O item a ser removido da **coleção \<T >** . Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|verdadeiro|A coleção da qual o item deve ser removido. Essa coleção é do tipo **ICollection < TypeArgument \>.** Para especificar a coleção, digite uma expressão de Visual Basic na grade de propriedades.|
|*TypeArgument*|verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Um valor que indica se o item especificado foi removido da coleção. Para especificar uma variável para associar ao resultado, digite uma variável na grade de propriedade|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)