---
title: Designer de Fluxo de Trabalho-designer de &lt; atividade T ClearCollection &gt;
description: Saiba como você pode usar o designer de <T> atividade ClearCollection para criar e configurar uma atividade ClearCollection <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31d576712804a75fdca57374ce82a53ff0d1ce84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942081"
---
# <a name="clearcollectiont-activity-designer"></a>Designer de atividade ClearCollection\<T>

O designer de atividade **ClearCollection \<T>** é usado para criar e configurar uma <xref:System.Activities.Statements.ClearCollection%601> atividade.

## <a name="the-clearcollectiont-activity"></a>A atividade ClearCollection \<T>

A atividade de <xref:System.Activities.Statements.ClearCollection%601> limpa especificada uma coleção de todos os itens.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usando o designer de \<T> atividade ClearCollection

O designer de atividade **ClearCollection \<T>** pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** do designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

O designer de atividade **ClearCollection \<T>** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde as atividades são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade cria uma <xref:System.Activities.Statements.ClearCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> clarocollection<Int32 \> . (Por padrão, o *TypeArgument* é **Int32**. TypeArgument pode ser alterado na grade de propriedades.) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade **clearcollection \><T** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-clearcollectiont-properties"></a>As propriedades ClearCollection \<T>

A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ClearCollection%601> e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ClearCollection%601> . O padrão é ClearCollection<Int32 \> . Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Especifica a coleção a ser limpa os itens. Esta coleção é do tipo **ICollection \<TypeArgument> .** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|True|Especifica o tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte também

- [Coleção](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)