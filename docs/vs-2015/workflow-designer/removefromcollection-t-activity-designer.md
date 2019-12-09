---
title: RemoveFromCollection &lt;T &gt; designer de atividade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672572"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>Designer de atividade do RemoveFromCollection &lt;T &gt;
O **RemoveFromCollection \<T >** designer de atividade é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.RemoveFromCollection%601>.

## <a name="the-removefromcollectiont-activity"></a>A atividade de > \<T do RemoveFromCollection
 A atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> remover um item específico de uma coleção específico.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Usando o designer de atividade do RemoveFromCollection \<T >
 O **RemoveFromCollection \<T >** designer de atividade pode ser encontrado na **categoria coleção** da **caixa de ferramentas**, que é acessada clicando na guia caixa de **ferramentas** em [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** em o menu **Exibir** ou CTRL + ALT + X.)

 O designer de atividade do **RemoveFromCollection \<T >** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> com uma <xref:System.Activities.Activity.DisplayName%2A> padrão de > de \<Int32 RemoveFromCollection. O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do **RemoveFromCollection \<T >** designer de atividade ou na caixa **DisplayName** da grade de propriedades. Outras propriedades devem ser editadas na grade de propriedade.

### <a name="the-removefromcollectiont-properties"></a>As propriedades de > \<T RemoveFromCollection
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.RemoveFromCollection%601> e descreve como elas são usadas no designer.

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.RemoveFromCollection%601> . O padrão é RemoveFromCollection \<Int32 >.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|verdadeiro|O item a ser adicionado à **coleção \<T >** . Este item é do tipo *T*, que é do tipo *TypeArgument*. Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|verdadeiro|A coleção para que o item deve ser adicionado. Esta coleção é do tipo **ICollection \<TypeArgument >.** Para especificar a coleção, digite uma expressão de Visual Basic na grade de propriedades.|
|*TypeArgument*|verdadeiro|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>. Por padrão, esse tipo de *TypeArgument* é definido como **Int32**. Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedades.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Um valor que indica se o item especificado foi removido da coleção. Para especificar uma variável para associar ao resultado, digite uma variável na grade de propriedade|

## <a name="see-also"></a>Consulte também
 [Coleta](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [clearcollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md)