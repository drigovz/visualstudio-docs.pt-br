---
title: Designer de atividade de CompensableActivity
description: Saiba como você pode usar o designer de atividade CompensableActivity no Designer de Fluxo de Trabalho para criar e configurar uma atividade CompensableActivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d05809b1e370fee2505470be1c06366f76bf9ca
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996221"
---
# <a name="compensableactivity-activity-designer"></a>Designer de atividade de CompensableActivity

O designer de atividade **CompensableActivity** é usado para criar e configurar uma <xref:System.Activities.Statements.CompensableActivity> atividade.

## <a name="the-compensableactivity-activity"></a>A atividade de CompensableActivity
 <xref:System.Activities.Statements.CompensableActivity> define uma unidade de trabalho que pode ser compensado confirmada ou após a conclusão com êxito.

### <a name="using-the-compensableactivity-activity-designer"></a>Usando o designer de atividade de CompensableActivity
 O designer de atividade **CompensableActivity** pode ser encontrado na categoria **transação** da **caixa de ferramentas**. Para abrir a **caixa de ferramentas**, selecione a guia caixa de **ferramentas** no lado esquerdo da designer de fluxo de trabalho. Como alternativa, selecione **caixa de ferramentas** no menu **Exibir** ou pressione **Ctrl** + **ALT** + **X**.

 O designer de atividade do **CompensableActivity** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho. Você pode remover o designer de atividade dentro de um <xref:System.Activities.Statements.Sequence> . Descartar o designer de atividade cria uma <xref:System.Activities.Statements.CompensableActivity> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de CompensableActivity. Edite o <xref:System.Activities.Activity.DisplayName%2A> valor no cabeçalho do designer de atividade **CompensableActivity** . Ele também pode ser editado na caixa **DisplayName** da grade de propriedades.

### <a name="the-compensableactivity-properties"></a>As propriedades de CompensableActivity
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.CompensableActivity> e descreve como elas são usadas no designer. A <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Activity%601.Result%2A> propriedade e pode ser editada na grade de propriedades, mas as outras propriedades devem ser editadas na superfície de designer de fluxo de trabalho.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável opcional de atividade de <xref:System.Activities.Statements.CompensableActivity> . O padrão é CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|Falso|Especifica o valor de retorno de <xref:System.Activities.Statements.CompensableActivity>. Esta propriedade deve ser editada na grade de propriedade.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Verdadeiro|Especifica a atividade para que a compensação, cancelamento, e a lógica de confirmação são fornecidos. Para adicionar a <xref:System.Activities.Statements.CompensableActivity.Body%2A> atividade, descartar uma atividade da caixa de **ferramentas** no **corpo** box no designer de atividade do **CompensableActivity** . Adicione o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|Falso|Especifica a atividade que é executada quando há um cancelamento. Para adicionar a atividade, descarte seu designer da caixa de **ferramentas** na **CancellationHandler** box no designer de atividade do **CompensableActivity** . Adicione o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|Falso|Especifica a atividade a ser executada para compensar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Compensate> .<br /><br /> Para adicionar a atividade, remova seu designer de atividade da caixa de **ferramentas** para o **CompensationHandler** box no designer de atividade do **CompensableActivity** . Adicione o texto de dica "soltar atividade aqui".|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|Falso|Especifica a atividade a ser executada para confirmar a atividade de <xref:System.Activities.Statements.CompensableActivity.Body%2A> . Esse manipulador pode ser chamado explicitamente usando a atividade de <xref:System.Activities.Statements.Confirm> .<br /><br /> Para adicionar a atividade, remova seu designer de atividade da caixa de **ferramentas** para o **ConfirmationHandler** box no designer de atividade do **CompensableActivity** . Adicione o texto de dica "soltar atividade aqui".|

## <a name="see-also"></a>Confira também

- [Transação](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensar](../workflow-designer/compensate-activity-designer.md)
- [Veja](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
