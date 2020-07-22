---
title: Designer de atividades Designer de Fluxo de Trabalho-ExistsInCollection &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b48bb11e2aac9d542a07551df62d710c41596d28
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875651"
---
# <a name="existsincollectiont-activity-designer"></a>Designer de atividade ExistsInCollection\<T>

O designer de atividade ** \<T> ExistsInCollection** é usado para criar e configurar uma <xref:System.Activities.Statements.ExistsInCollection%601> atividade.

## <a name="the-existsincollectiont-activity"></a>A \<T> atividade ExistsInCollection

A atividade de <xref:System.Activities.Statements.ExistsInCollection%601> determina se um item específico existe em uma coleção específico.

### <a name="using-the-existsincollectiont-activity-designer"></a>Usando o \<T> Designer de atividade ExistsInCollection

O designer de atividade do **ExistsInCollection \<T> ** pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** do designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

O designer de atividade do **ExistsInCollection \<T> ** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.ExistsInCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de ExistsInCollection<Int32 \> . (Por padrão, o *TypeArgument* é **Int32**. Ele pode ser alterado na grade de propriedades.)  O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **ExistsInCollection<T \> ** Activity Designer ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-existsincollectiont-properties"></a>As \<T> Propriedades ExistsInCollection

A tabela a seguir mostra as <xref:System.Activities.Statements.ExistsInCollection%601> Propriedades e descreve como elas são usadas no designer:

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.ExistsInCollection%601> . O padrão é ExistsInCollection<Int32 \> . Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Verdadeiro|O item a ser pesquisado na coleção \<T> . Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Verdadeiro|A coleção na qual verificar se o item existe. Essa coleção é do tipo **ICollection<TypeArgument \> .** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|Verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Um valor que indica se o item especificado existe na coleção. Para especificar uma variável para associar ao resultado, digite uma variável do Visual Basic na grade de propriedade.|

## <a name="see-also"></a>Veja também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)