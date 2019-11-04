---
title: Designer de atividade do CancellationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659177"
---
# <a name="cancellationscope-activity-designer"></a>Designer de atividade de CancellationScope
O designer de atividade **CancellationScope** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>A atividade de CancellationScope
 A atividade de <xref:System.Activities.Statements.CancellationScope> permite que você especifique uma atividade para a lógica de execução e cancelar para a atividade.

### <a name="using-the-cancellationscope-activity-designer"></a>Usando o designer de atividade de CancellationScope
 O designer de atividade do **CancellationScope** pode ser encontrado na categoria **transação** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** da [!INCLUDE[wfd2](../includes/wfd2-md.md)] (como alternativa, selecione **barra de ferramentas** na **exibição** menu ou CTRL + ALT + X.)

 O designer de atividade do **CancellationScope** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence>. Isso cria uma atividade de <xref:System.Activities.Statements.CancellationScope> com <xref:System.Activities.Activity.DisplayName%2A> padrão de CancellationScope. O valor <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **CancellationScope** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-cancellationscope-properties"></a>As propriedades de CancellationScope
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CancellationScope> e descreve como elas são usadas no designer. A propriedade de <xref:System.Activities.Activity.DisplayName%2A> pode ser editada na grade de propriedade mas outras propriedades devem ser editadas na superfície de [!INCLUDE[wfd2](../includes/wfd2-md.md)] .

|Nome da Propriedade|Necessária|Uso|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CancellationScope> . O padrão é CancellationScope. Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Especifica a atividade para que a lógica cancelar é fornecida. Para adicionar a atividade de <xref:System.Activities.Statements.CancellationScope.Body%2A>, descarte uma atividade da caixa de **ferramentas** no **corpo** do **CancellationScope** do designer de atividades com dica de texto "soltar atividade aqui".|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Especifica a atividade que é executado no caso de cancelamento. Para adicionar a atividade de <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, descarte uma atividade da caixa de **ferramentas** no **CancellationHandler** box no designer de atividade **CancellationScope** com o texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Consulte também
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) de [confirmação](../workflow-designer/confirm-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) de [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) de [transação](../workflow-designer/transaction-activity-designers.md)