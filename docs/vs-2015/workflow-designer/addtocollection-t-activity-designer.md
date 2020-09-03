---
title: Designer de atividade do AddToCollection &lt; T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659201"
---
# <a name="addtocollectionlttgt-activity-designer"></a>Designer de atividade do AddToCollection &lt; T &gt;
O designer de atividade ** \<T> AddToCollection** é usado para criar e configurar uma <xref:System.Activities.Statements.AddToCollection%601> atividade.

## <a name="the-addtocollectiont-activity"></a>A \<T> atividade AddToCollection
 A atividade de <xref:System.Activities.Statements.AddToCollection%601> adiciona um item a uma coleção.

### <a name="using-the-addtocollectiont-activity-designer"></a>Usando o \<T> Designer de atividade AddToCollection
 O designer de atividade do **AddToCollection \<T> ** pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** do [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade do **AddToCollection \<T> ** pode ser arrastado da **caixa de ferramentas** e descartado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.AddToCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de AddToCollection \<Int32> . (Por padrão, o *TypeArgument* é **Int32**. Isso pode ser alterado na grade de propriedades.) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade **AddToCollection \<T> ** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-addtocollectiont-properties"></a>As \<T> Propriedades AddToCollection
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.AddToCollection%601> e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável de atividade de <xref:System.Activities.Statements.AddToCollection%601> . O padrão é AddToCollection \<Int32> . Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Verdadeiro|O item a ser adicionado à coleção \<T> . Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Verdadeiro|A coleção para que o item deve ser adicionado. Esta coleção é do tipo **ICollection \<TypeArgument> **. Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|Verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte Também
 [Coleção](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [Designer de atividade \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) ClearCollection ExistsInCollection [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md) [ \<T> ](../workflow-designer/clearcollection-t-activity-designer.md)