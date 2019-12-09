---
title: Caixa de diálogo Designer de Fluxo de Trabalho-adicionar CorrelationInitializers
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d69b53e21d11cba99a9e897871c6f9e0320352f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650768"
---
# <a name="add-correlationinitializers-dialog-box"></a>Adicione a caixa de diálogo CorrelationInitializers

A caixa de diálogo **Adicionar inicializadores de correlação** é usada em Designer de fluxo de trabalho para configurar as propriedades de **CorrelationInitializers** das atividades <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>. Para obter mais informações sobre os designers de atividade que usam essa caixa, consulte os tópicos [Enviar](../workflow-designer/send-activity-designer.md), [receber](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

Os inicializadores de correlação na coleção especificada com essa caixa de diálogo podem inicializar as seguintes correlações entre as atividades de mensagens:

- baseado em consulta
- contexto
- contexto de retorno de chamada
- solicitação-resposta

A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **Adicionar inicializadores de correlação** :

|Elemento da Interface do Usuário|Descrição|
|-|-----------------|
|**Adicionar inicializador**|Clique na caixa **Adicionar inicialização** para adicionar um inicializador adicional à coleção.|
|**Tipo de correlação**|Especifica o tipo de inicializador de correlação. Há quatro tipos a escolher:<br /><br /> 1. um inicializador de correlação de retorno de chamada para especificar um <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2. um inicializador de correlação de contexto para especificar um <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3. um inicializador de correlação de solicitação-resposta para especificar um <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4. um inicializador de correlação de consulta para especificar um <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Para editar o **Correlationtype**<br /><br /> 1. Tab para a linha específica no DataGrid do **inicializador de adição** .<br />2. para definir o foco como **CorrelationTypeComboBox**, pressione **Ctrl** +**Tab**.<br />3. Pressione Alt + seta para baixo para exibir a **ComboBox** e editá-la.|
|**Consultas XPath**|Um par chave/valor que contém as consultas usadas para extrair dados de correlação das mensagens de entrada e saída. Esta lista só é válido para usar <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> tipos.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>Para iniciar a caixa de diálogo de inicializadores de adicionar correlação

 A caixa de diálogo **Adicionar inicializadores de correlação** é usada pelos designers **Enviar**, **receber**, **ReceiveAndSendReply**e **SendAndReceiveReply** . Acessá-los é semelhante em cada caso, e o caso que envolve o designer de **recebimento** é usado aqui para ilustrar o procedimento.

 O designer de atividade de **recebimento** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho onde as atividades são colocadas. Descartar o designer de atividade de **recebimento** cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com um <xref:System.Activities.Activity.DisplayName%2A> de recebimento padrão. Selecione o designer de atividade de **recebimento** e clique no botão de reticências ao lado do texto (coleção) da propriedade **CorrelationInitializers** na grade de propriedades para que a caixa de diálogo **Adicionar inicializadores de correlação** seja exibida.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Inicializar Correlação](../workflow-designer/initialize-correlation-dialog-box.md)