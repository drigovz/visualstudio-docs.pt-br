---
title: Designer de Fluxo de Trabalho-confirmar designer de atividade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abd7fedd958072baf23b456f9897ab67c864991d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86876132"
---
# <a name="confirm-activity-designer"></a>Confirme que o designer de atividades

O designer de atividade de **confirmação** é usado para criar e configurar uma <xref:System.Activities.Statements.Confirm> atividade.

## <a name="the-confirm-activity"></a>A atividade de confirmação
 A atividade de <xref:System.Activities.Statements.Confirm> chama explicitamente <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> para uma atividade contida em <xref:System.Activities.Statements.CompensableActivity>. Se a atividade de <xref:System.Activities.Statements.Confirm> não é usada dentro de <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> de <xref:System.Activities.Statements.CompensableActivity>, então você deve especificar a propriedade de <xref:System.Activities.Statements.Confirm.Target%2A> .

 <xref:System.Activities.Statements.CompensationToken> especificado por <xref:System.Activities.Statements.Compensate.Target%2A> fornece um meio para confirmar ou compensar explicitamente <xref:System.Activities.Statements.CompensableActivity> uma vez que <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> terminou com êxito.

### <a name="using-the-confirm-activity-designer"></a>Usando o designer de atividade de confirmação
 O designer de atividade de **confirmação** pode ser encontrado na categoria **transação** da **caixa de ferramentas**, que é acessada clicando na guia **caixa de ferramentas** no lado esquerdo da designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

 O designer de atividade de **confirmação** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas, como dentro de um <xref:System.Activities.Statements.Sequence> . Isso cria uma atividade de <xref:System.Activities.Statements.Confirm> com <xref:System.Activities.Activity.DisplayName%2A> padrão Confirmar. O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do designer de atividade de **confirmação** ou na caixa **DisplayName** da grade de propriedades.

### <a name="the-confirm-properties"></a>As propriedades de confirmação
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Confirm> e descreve como elas são usadas no designer. A <xref:System.Activities.Activity.DisplayName%2A> propriedade pode ser editada na grade de propriedades ou na superfície designer de fluxo de trabalho, mas a <xref:System.Activities.Statements.Confirm.Target%2A> propriedade deve ser editada na grade de propriedades.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.CancellationScope> . O padrão é confirma.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|Verdadeiro|Especifica <xref:System.Activities.InArgument%601> que contém <xref:System.Activities.Statements.CompensationToken> para esta atividade de <xref:System.Activities.Statements.Confirm> .|

## <a name="see-also"></a>Confira também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)