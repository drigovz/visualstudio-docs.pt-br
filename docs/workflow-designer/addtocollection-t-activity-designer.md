---
title: Designer de Fluxo de Trabalho-AddToCollection<T> designer de atividade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb00679001cc09b8fdfa68f898923ac208b32c4e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115320"
---
# <a name="addtocollectiont-activity-designer"></a>Designer de atividade do AddToCollection\<T >

O designer de atividade **AddToCollection\<t >** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.AddToCollection%601>.

## <a name="the-addtocollectiont-activity"></a>A atividade AddToCollection\<T >

A atividade de <xref:System.Activities.Statements.AddToCollection%601> adiciona um item a uma coleção.

### <a name="using-the-addtocollectiont-activity-designer"></a>Usando o designer de atividades AddToCollection\<T >

O designer de atividades **AddToCollection\<t >** pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** da designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl**+**ALT**+**X**.

O designer de atividades **AddToCollection\<t >** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde as atividades são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o **AddToCollection\<t >** Activity Designer cria uma atividade <xref:System.Activities.Statements.AddToCollection%601> com uma <xref:System.Activities.Activity.DisplayName%2A> padrão de < Int32 AddToCollection\>. (Por padrão, o *TypeArgument* é **Int32**. TypeArgument pode ser alterado na grade de propriedades.) O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade do **AddToCollection < t\>** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-addtocollectiont-properties"></a>As Propriedades AddToCollection\<T >

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.AddToCollection%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessário|Medição de|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.AddToCollection%601> . O padrão é AddToCollection < Int32\>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|verdadeiro|O item a ser adicionado à coleção\<T >. Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|verdadeiro|A coleção para que o item deve ser adicionado. Essa coleção é do tipo **ICollection < TypeArgument\>** . Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Veja também

- [Coleta](../workflow-designer/collection-activity-designers.md)
- [Designer de atividade do AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
