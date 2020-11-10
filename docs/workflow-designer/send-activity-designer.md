---
title: Designer de Fluxo de Trabalho-enviar designer de atividade
description: Saiba mais sobre a atividade enviar e como você pode usar o designer de atividade de envio para criar e configurar uma atividade enviar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78925411f911f9c0dfc0c2cfff891deca0e91e3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434045"
---
# <a name="send-activity-designer"></a>Enviar o designer de atividades

O designer de atividade de **envio** é usado para criar e configurar uma <xref:System.ServiceModel.Activities.Send> atividade.

## <a name="the-send-activity"></a>Atividade de enviar

 Uma atividade de <xref:System.ServiceModel.Activities.Send> é usada para enviar uma mensagem a um serviço. Uma atividade de <xref:System.ServiceModel.Activities.ReceiveReply> pode ser associada a uma atividade de <xref:System.ServiceModel.Activities.Send> que receberá uma mensagem como parte de um padrão de troca de solicitação/resposta de mensagem no cliente.

### <a name="using-the-send-activity-designer"></a>Usando o designer de atividade de enviar

Acesse o designer de atividade de **envio** na categoria **mensagens** da **caixa de ferramentas**. O designer de atividade de **envio** pode ser arrastado da **caixa de ferramentas** e descartado para a superfície de designer de fluxo de trabalho sempre que as atividades são geralmente colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Send> com uma opção <xref:System.Activities.Activity.DisplayName%2A> de enviar. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **envio** ou na caixa **DisplayName** da grade de propriedades.

Para criar uma <xref:System.ServiceModel.Activities.ReceiveReply> atividade e associá-la à <xref:System.ServiceModel.Activities.Send> atividade selecionada, clique com o botão direito do mouse no designer de atividade de **envio** , clique no item **criar ReceiveReply** no menu de contexto e o designer de **ReceiveReplyForSend** aparecerá abaixo do designer de **envio** . A atividade de <xref:System.ServiceModel.Activities.ReceiveReply> é uma atividade que receberá uma mensagem como parte de um padrão de troca de solicitação/resposta de mensagem no cliente. Ele pode ser configurado com o designer de **ReceiveReplyForSend** .

Como alternativa, o designer de modelos **SendAndReceiveReply** na categoria **mensagens** da **caixa de ferramentas** pode ser usado para criar um par de atividades pré-configuradas e predefinidas <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply> . Para obter mais informações sobre o uso dos modelos **SendAndReceiveReply** e **ReceiveReplyForSend** , consulte o tópico [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>As propriedades de atividade de enviar

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.Send> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades ou na superfície Designer de Fluxo de Trabalho.

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | O nome amigável de atividade de <xref:System.ServiceModel.Activities.Send> . O padrão é enviar. Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Verdadeiro | O nome da operação de serviço chamada por esta atividade de <xref:System.ServiceModel.Activities.Send> . Essa propriedade é usada para construir o valor padrão para a propriedade **Action** se a propriedade **Action** não estiver definida explicitamente. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Verdadeiro | O nome do contrato de serviço que o serviço ser chamado implementa. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite essa propriedade selecionando o botão de reticências ao lado do campo **conteúdo** na grade de propriedades ou clicando no botão **definir...** ao lado do rótulo **conteúdo** na superfície do designer de atividade **receber** . Ambos exibem a caixa de diálogo **definição de conteúdo** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Definição de conteúdo](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Falso | Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para rotear a mensagem à instância apropriado de fluxo de trabalho.<br /><br /> Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Editor de expressão** . Para obter mais informações sobre o uso dessa caixa de diálogo, consulte o tópico [como: usar o editor de expressão](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Send> dentro de fluxo de trabalho. Clique no botão de reticências ao lado da <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> Propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar inicializadores de correlação** . Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Adicionar CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Falso | Uma coleção de tipos conhecidos para que a operação de serviço é chamada por esta atividade de <xref:System.ServiceModel.Activities.Send> . Esta propriedade deve ser usada em conjunto com a propriedade de <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> definida como <xref:System.Runtime.Serialization.DataContractSerializer>. É ignorada se <xref:System.Xml.Serialization.XmlSerializer> é usado.<br /><br /> Selecione o botão de reticências ao lado do campo **KnownTypes** na grade de propriedades para exibir a caixa de diálogo **Editor de coleção de tipos** com a qual você pode adicionar tipos relevantes.<br /><br /> Selecione o botão de reticências ao lado do campo **KnownTypes** na grade de propriedades para exibir a caixa de diálogo **Editor de coleção de tipos** com a qual você pode adicionar tipos relevantes. Para obter mais informações sobre como usar essa caixa, consulte o tópico da [caixa de diálogo Editor de coleção de tipos](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Verdadeiro | Especifica <xref:System.Net.Security.ProtectionLevel> para a mensagem.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> significa somente autenticação.<br />2.  <xref:System.Net.Security.ProtectionLevel> significa assinar dados para ajudar a garantir a integridade dos dados transmitidos.<br />3.  <xref:System.Net.Security.ProtectionLevel> significa criptografar e assinar dados para ajudar a garantir a confidencialidade e a integridade dos dados transmitidos. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Verdadeiro | O serializador usar para que a operação de serviço é chamada pela atividade de <xref:System.ServiceModel.Activities.Send> . O valor padrão é <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa e desserializa uma instância de um tipo em um fluxo XML ou em um documento usando um contrato fornecido de dados. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se ele não estiver definido explicitamente, seu valor padrão será: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Se especificado em uma atividade de <xref:System.ServiceModel.Activities.Send> , a atividade de <xref:System.ServiceModel.Activities.Receive> que recebe a mensagem deve ter o mesmo valor para que a mensagem é entregada corretamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel> permitido o receptor de mensagem. Ele define os níveis de representação de segurança, que controlam o grau em que um processo de servidor pode agir em nome de um processo de cliente.<xref:System.Security.Principal.TokenImpersonationLevel>  indica que um nível da representação não é atribuído. <xref:System.Security.Principal.TokenImpersonationLevel> indica que o processo do servidor não pode obter informações de identificação sobre o cliente e não pode representar o cliente. <xref:System.Security.Principal.TokenImpersonationLevel> indica que o processo do servidor pode obter informações sobre o cliente, como identificadores de segurança e privilégios, mas que ele não pode representar o cliente. Isso é útil para servidores que exportam seus próprios objetos, por exemplo, os produtos de base de dados que exporte tabelas e modos de exibição. Usando informações recuperadas de cliente segurança, o servidor pode tomar decisões de acesso de validação não poderá usar outros serviços usando o contexto de segurança do cliente. <xref:System.Security.Principal.TokenImpersonationLevel> indica que o processo do servidor pode representar o contexto de segurança do cliente em seu sistema local. O servidor não pode representar o cliente em sistemas remotos. <xref:System.Security.Principal.TokenImpersonationLevel> indica que o processo do servidor pode representar o contexto de segurança do cliente em sistemas remotos. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> que a atividade de <xref:System.ServiceModel.Activities.Send> envia à mensagem. Se essa propriedade for definida, a <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> Propriedade deverá ser **nula**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress> que a mensagem é enviada. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | O nome da configuração do ponto de extremidade. Essa propriedade é definida quando você estiver configurando um ponto de extremidade em um arquivo de configuração. Essa propriedade deve ser definida como o nome fornecido no **\<endpoint>** elemento no arquivo de configuração. Se essa propriedade for definida, a <xref:System.ServiceModel.Activities.Send.Endpoint%2A> Propriedade deverá ser **nula**. |

## <a name="see-also"></a>Confira também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Recebe](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)