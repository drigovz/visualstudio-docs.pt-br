---
title: Caixa de diálogo Adicionar CorrelationInitializers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e1402b90dfc78068546b510ce6b85379b1695f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672033"
---
# <a name="add-correlationinitializers-dialog-box"></a>Adicione a caixa de diálogo CorrelationInitializers
A caixa de diálogo **Adicionar inicializadores de correlação** é usada no [!INCLUDE[wfd1](../includes/wfd1-md.md)] para configurar as propriedades **CorrelationInitializers** das <xref:System.ServiceModel.Activities.Send> atividades,, <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply> . [!INCLUDE[crabout](../includes/crabout-md.md)] os designers de atividade que usam essa caixa, confira os tópicos [Enviar](../workflow-designer/send-activity-designer.md), [receber](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

 Inicializadores de correlação na coleção especificada com esta caixa de diálogo pode inicializar a consulta com base, o contexto, o contexto de retorno de chamada, ou se correlaciona de solicitação de resposta entre as atividades de mensagem.

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **Adicionar inicializadores de correlação** .

|Elemento da interface do usuário|Descrição|
|----------------|-----------------|
|**Adicione o inicializador**|Clique na caixa **Adicionar inicialização** para adicionar um inicializador adicional à coleção.|
|**Tipo de correlação**|Especifica o tipo de inicializador de correlação. Há quatro tipos a escolher:<br /><br /> 1. um inicializador de correlação de retorno de chamada para especificar um <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. um inicializador de correlação de contexto para especificar um <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. um inicializador de correlação de solicitação-resposta para especificar um <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. um inicializador de correlação de consulta para especificar um <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> Para editar o **Correlationtype**<br /><br /> 1. Tab para a linha específica no DataGrid do **inicializador de adição** .<br />2. Pressione Ctrl + Tab para definir o foco como **CorrelationTypeComboBox**<br />3. Pressione Alt + seta para baixo para exibir a **ComboBox** e editá-la.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada e saída. Esta lista só é válido para usar <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> tipos.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar a caixa de diálogo de inicializadores de adicionar correlação
 A caixa de diálogo **Adicionar inicializadores de correlação** é usada pelos designers **Enviar**, **receber**, **ReceiveAndSendReply**e **SendAndReceiveReply** . Acessá-los é semelhante em cada caso e o caso que envolve o designer de **recebimento** é usado aqui para ilustrar o procedimento.

 O designer de atividade **Receive** pode ser arrastado da **caixa de ferramentas** e retirado para a [!INCLUDE[wfd2](../includes/wfd2-md.md)] superfície onde as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. Selecione o designer de atividade de **recebimento** e clique no botão de reticências ao lado do texto (coleção) da propriedade **CorrelationInitializers** na grade de propriedades para que a caixa de diálogo **Adicionar inicializadores de correlação** seja exibida.

## <a name="see-also"></a>Consulte Também
 [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)