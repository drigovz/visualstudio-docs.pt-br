---
title: Designer de Fluxo de Trabalho-ClearCollection <T> designer de atividade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4808c046c4da23bc5c95d3978965afd938962f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650695"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection \<T > designer de atividade

O **\<T clearcollection >** designer de atividade é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.ClearCollection%601>.

## <a name="the-clearcollectiont-activity"></a>A atividade de > de \<T ClearCollection

A atividade de <xref:System.Activities.Statements.ClearCollection%601> limpa especificada uma coleção de todos os itens.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usando o \<T ClearCollection > designer de atividade

O designer de atividade de **> de limpezacollection \<T** pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** da designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** +**ALT** +**X**.

O **\<T clearcollection >** designer de atividade pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Descartar o designer de atividade cria uma atividade de <xref:System.Activities.Statements.ClearCollection%601> com um <xref:System.Activities.Activity.DisplayName%2A> padrão de ClearCollection < Int32 \>. (Por padrão, o *TypeArgument* é **Int32**. TypeArgument pode ser alterado na grade de propriedades.) O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **clearcollection < t \>** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-clearcollectiont-properties"></a>As propriedades de > ClearCollection \<T

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ClearCollection%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ClearCollection%601> . O padrão é ClearCollection < Int32 \>. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|verdadeiro|Especifica a coleção a ser limpa os itens. Esta coleção é do tipo **ICollection \<TypeArgument >.** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|verdadeiro|Especifica o tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)