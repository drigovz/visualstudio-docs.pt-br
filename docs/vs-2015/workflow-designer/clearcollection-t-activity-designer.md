---
title: ClearCollection &lt; T &gt; Designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657017"
---
# <a name="clearcollectionlttgt-activity-designer"></a>Limpar o &lt; &gt; Designer de atividade T
O designer de atividade **ClearCollection \<T> ** é usado para criar e configurar uma <xref:System.Activities.Statements.ClearCollection%601> atividade.

## <a name="the-clearcollectiont-activity"></a>A atividade ClearCollection \<T>
 A atividade de <xref:System.Activities.Statements.ClearCollection%601> limpa especificada uma coleção de todos os itens.

### <a name="using-the-clearcollectiont-activity-designer"></a>Usando o designer de \<T> atividade ClearCollection
 O designer de atividade **ClearCollection \<T> ** pode ser encontrado na categoria **coleção** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** do [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** no menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade ** \<T> ClearCollection** pode ser arrastado da **caixa de ferramentas** e descartado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície onde as atividades geralmente são colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma <xref:System.Activities.Statements.ClearCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de ClearCollection \<Int32> . (Por padrão, o *TypeArgument* é **Int32**. Isso pode ser alterado na grade de propriedades.) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade ** \<T> ClearCollection** ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-clearcollectiont-properties"></a>As propriedades ClearCollection \<T>
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ClearCollection%601> e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ClearCollection%601> . O padrão é ClearCollection \<Int32> . Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Verdadeiro|Especifica a coleção a ser limpa os itens. Esta coleção é do tipo **ICollection \<TypeArgument> .** Para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|
|*TypeArgument*|Verdadeiro|Especifica o tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|

## <a name="see-also"></a>Consulte Também
 [Collection](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)