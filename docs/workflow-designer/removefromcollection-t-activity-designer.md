---
title: Designer de atividade do RemoveFromCollection &lt; T &gt;
description: Em Designer de Fluxo de Trabalho, saiba como usar o designer de <T> atividade RemoveFromCollection para criar e configurar uma <T> atividade RemoveFromCollection.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fdaf7172c00d80e5e7615bfcadcc1fb6233c257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847356"
---
# <a name="removefromcollectiont-activity-designer"></a>Designer de atividade RemoveFromCollection\<T>

O designer de atividade **\<T> RemoveFromCollection** é usado para criar e configurar uma <xref:System.Activities.Statements.RemoveFromCollection%601> atividade.

## <a name="the-removefromcollectiontactivity"></a>A \<T> atividade RemoveFromCollection

A atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> remover um item específico de uma coleção específico.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usando o \<T> Designer de atividade RemoveFromCollection

Acesse o designer de atividade do **RemoveFromCollection \<T>** na categoria **coleção** da **caixa de ferramentas**.
O designer de atividade do **RemoveFromCollection \<T>** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.RemoveFromCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de RemoveFromCollection<Int32 \> . O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **RemoveFromCollection<T \>** Activity Designer ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-removefromcollectiont-properties"></a>As Propriedades RemoveFromCollection<T \>

A tabela a seguir mostra as <xref:System.Activities.Statements.RemoveFromCollection%601> Propriedades e descreve como elas são usadas no designer:

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável opcional de atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> . O padrão é RemoveFromCollection<Int32 \> .<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|O item a ser removido da **coleção \<T>**. Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|A coleção da qual o item deve ser removido. Essa coleção é do tipo **ICollection<TypeArgument \> .** Para especificar a coleção, digite uma expressão de Visual Basic na grade de propriedades.|
|*TypeArgument*|True|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Um valor que indica se o item especificado foi removido da coleção. Para especificar uma variável para associar ao resultado, digite uma variável na grade de propriedade|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)