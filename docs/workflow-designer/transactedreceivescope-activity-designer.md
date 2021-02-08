---
title: Designer de atividade TransactedReceiveScope
description: No Designer de Fluxo de Trabalho, saiba como você pode usar o designer de TransactedReceiveScope para criar e configurar uma atividade TransactedReceiveScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eceb0776fd1cb5e850dab2b97ab6e7e56a684ebd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838016"
---
# <a name="transactedreceivescope-activity-designer"></a>Designer de atividade de TransactedReceiveScope

O designer de **TransactedReceiveScope** é usado para criar e configurar uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade.

## <a name="the-transactedreceivescope-activity"></a>A atividade de TransactedReceiveScope

A atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> permite que você fluxo uma transação nas transações de servidor criadas por um fluxo de trabalho ou por um distribuidor.

### <a name="using-the-transactedreceivescope-activity-designer"></a>Usando o designer de atividade de TransactedReceiveScope

Acesse o designer de atividade **TransactedReceiveScope** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade **TransactedReceiveScope** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. Isso cria uma <xref:System.ServiceModel.Activities.TransactedReceiveScope> atividade com um **DisplayName** padrão de TransactedReceiveScope. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade **TransactedReceiveScope** ou na caixa **DisplayName** da grade de propriedades.

O designer de **TransactedReceiveScope** contém caixas de **solicitação** e **corpo** . Esses são usados para configurar a propriedade de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> , que especifica uma atividade de <xref:System.ServiceModel.Activities.Receive> e uma propriedade de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> , que especifica algum outro <xref:System.Activities.Activity>. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> cria uma transação. A transação é feita em ambientes para o escopo de <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> de modo que quaisquer atividades dentro desse escopo seja executado dentro desta transação.

### <a name="the-transactedreceivescope-properties"></a>As propriedades de TransactedReceiveScope

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.TransactedReceiveScope> e descreve como elas são usadas no designer. Essas <xref:System.Activities.Activity.DisplayName%2A> Propriedades podem ser editadas na grade de propriedades ou na superfície designer de fluxo de trabalho, mas as outras devem ser editadas na superfície de design.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|O nome amigável opcional de atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> . O padrão é TransactedReceiveScope.<br /><br /> Embora o nome de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um nome para exibição.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Descarta uma <xref:System.ServiceModel.Activities.Receive> atividade no bloco de **solicitação** na superfície do designer de atividade.|
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|Falso|Descarta um <xref:System.Activities.Activity> no bloco **Body** na superfície do designer de atividade.|

## <a name="see-also"></a>Confira também

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [Recebe](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)