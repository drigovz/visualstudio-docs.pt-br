---
title: Designer de atividade de Designer de Fluxo de Trabalho receber
description: Saiba mais sobre a atividade Receive e como usar o designer de atividade Receive para criar e configurar uma atividade Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6414d92cea867a1235d73a39b6415ab884651ec
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434188"
---
# <a name="receive-activity-designer"></a>Recebe o designer de atividades

O designer de atividade de **recebimento** é usado para criar e configurar uma <xref:System.ServiceModel.Activities.Receive> atividade. Uma atividade de <xref:System.ServiceModel.Activities.Receive> é uma atividade que receberá uma mensagem que pode ser um tipo interno como <xref:System.ServiceModel.Channels.Message>, <xref:System.IO.Stream> ou <xref:System.Xml.Linq.XElement>, ou um contrato definido de dados, o contrato de mensagem, ou a classe XML que pode ser serializada.

## <a name="the-receive-activity"></a>A atividade de receptor

A atividade de <xref:System.ServiceModel.Activities.Receive> pode receber um item único ou vários itens dependendo do tipo de recebem o conteúdo usado. Uma atividade de <xref:System.ServiceModel.Activities.SendReply> pode ser associada a uma atividade de <xref:System.ServiceModel.Activities.Receive> que receberá uma mensagem como parte de um padrão de troca de solicitação/resposta de mensagem no serviço.

### <a name="using-the-receive-activity-designer"></a>Usando o designer de atividade de receptor

Acesse o designer de atividade de **recebimento** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade **Receive** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Receive> com <xref:System.Activities.Activity.DisplayName%2A> padrão Receive. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **recebimento** ou na caixa **DisplayName** da grade de propriedades.

Para criar uma <xref:System.ServiceModel.Activities.SendReply> atividade e associá-la à <xref:System.ServiceModel.Activities.Receive> atividade selecionada, clique com o botão direito do mouse no designer de atividade de **recebimento** , clique no item **criar SendReply** no menu de contexto e o designer de **SendReplyToReceive** aparecerá abaixo do designer de **recebimento** . A atividade de <xref:System.ServiceModel.Activities.SendReply> é uma atividade que envia a mensagem de resposta como parte de um padrão de troca de solicitação/resposta de mensagem no serviço. Ele pode ser configurado com o designer de **SendReplyToReceive** .

Como alternativa, o designer de modelos **ReceiveAndSendReply** na categoria **mensagens** da **caixa de ferramentas** pode ser usado para criar um par de <xref:System.ServiceModel.Activities.Receive> atividade e pré-configurada <xref:System.ServiceModel.Activities.SendReply> . Para obter mais informações sobre o uso do modelo **ReceiveAndSendReply** e **SendReplyToReceive** , consulte o tópico [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) .

### <a name="the-receive-activity-properties"></a>As propriedades de atividade de receptor

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.Receive> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades ou na superfície de Designer de Fluxo de Trabalho. A única propriedade necessário é a propriedade de <xref:System.ServiceModel.Activities.Receive.OperationName%2A> .

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | Especifica o nome amigável de atividade de <xref:System.ServiceModel.Activities.Receive> . O valor padrão é receber.<br /><br /> Embora o uso de um valor não padrão para <xref:System.Activities.Activity.DisplayName%2A> amigável não é necessário restrita, é uma prática recomendada usar um valor. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | Verdadeiro | Especifica o nome da operação de serviço implementada por esta atividade de <xref:System.ServiceModel.Activities.Receive> . Essa propriedade é usada para construir o valor padrão para a propriedade **Action** se a propriedade **Action** não estiver definida explicitamente. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | Falso | Especifica o nome do contrato de serviço. Essa propriedade é usada para agrupar operações de serviço em contratos de serviço individuais. Todas as atividades de <xref:System.ServiceModel.Activities.Receive> que têm mesmo <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> são agrupadas no mesmo contrato de serviço (tipo de porta de WSDL.) O valor padrão é o nome CLR totalmente qualificado da atividade de nível superior (raiz). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade selecionando o botão de reticências ao lado do campo **conteúdo** na grade de propriedades ou clicando no botão **definir...** ao lado do rótulo **conteúdo** na superfície do designer de atividade **receber** . Ambos exibem a caixa de diálogo **definição de conteúdo** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | Falso | Especifica se correlaciona entre atividades de <xref:System.ServiceModel.Activities.Receive> em operações de serviço de um fluxo de trabalho com um objeto de <xref:System.ServiceModel.MessageQuerySet> . Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **definição de CorrelatesOn** . Para obter mais informações sobre o uso dessa caixa de diálogo, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | Falso | Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para rotear a mensagem à instância apropriado de fluxo de trabalho.<br /><br /> Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Editor de expressão** . Para obter mais informações sobre o uso dessa caixa de diálogo, consulte o tópico [como: usar o editor de expressão](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Receive> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | Falso | Especifica um valor que determina se uma nova instância de fluxo de trabalho é criada para processar a mensagem se a mensagem não correlaciona a uma instância existente de fluxo de trabalho. Se o valor for definido como **true** , uma nova instância de fluxo de trabalho será criada para processar a mensagem quando a mensagem não estiver correlacionada com uma instância de fluxo de trabalho existente. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | Falso | Especifica uma coleção de tipos conhecidos para a operação de serviço implementada por esta atividade de <xref:System.ServiceModel.Activities.Receive> . Esta propriedade deve ser usada em conjunto com a propriedade de <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> definida como <xref:System.Runtime.Serialization.DataContractSerializer>. É ignorada se <xref:System.Xml.Serialization.XmlSerializer> é usado.<br /><br /> Selecione o botão de reticências ao lado do campo **KnownTypes** na grade de propriedades para exibir a caixa de diálogo **Editor de coleção de tipos** com a qual você pode adicionar tipos relevantes. Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | Falso | Especifica <xref:System.Net.Security.ProtectionLevel> para a mensagem.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> significa somente autenticação.<br />2.  <xref:System.Net.Security.ProtectionLevel> significa assinar dados para ajudar a garantir a integridade dos dados transmitidos.<br />3.  <xref:System.Net.Security.ProtectionLevel> significa criptografar e assinar dados para ajudar a garantir a confidencialidade e a integridade dos dados transmitidos. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | Falso | Especifica o tipo de serializador para usar a operação de serviço implementada pela atividade de <xref:System.ServiceModel.Activities.Receive> . O valor padrão é <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa e desserializa uma instância de um tipo em um fluxo XML ou em um documento que usa um contrato fornecido de dados. <xref:System.Xml.Serialization.XmlSerializer> também pode ser usado se mais controle sobre é necessário XML. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se ele não estiver definido explicitamente, seu valor padrão será: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . |

## <a name="see-also"></a>Confira também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Enviar](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
