---
title: Designer de fluxo de trabalho - Enviar designer de atividades
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395217"
---
# <a name="send-activity-designer"></a>Enviar o designer de atividades

O **designer de** atividades Send é <xref:System.ServiceModel.Activities.Send> usado para criar e configurar uma atividade.

## <a name="the-send-activity"></a>Atividade de enviar

 Uma atividade de <xref:System.ServiceModel.Activities.Send> é usada para enviar uma mensagem a um serviço. Uma atividade de <xref:System.ServiceModel.Activities.ReceiveReply> pode ser associada a uma atividade de <xref:System.ServiceModel.Activities.Send> que receberá uma mensagem como parte de um padrão de troca de solicitação/resposta de mensagem no cliente.

### <a name="using-the-send-activity-designer"></a>Usando o designer de atividade de enviar

Acesse o designer de atividades **Enviar** na categoria **Mensagens** da Caixa de **Ferramentas**. O designer de atividades **Send** pode ser arrastado da caixa de **ferramentas** e jogado na superfície do Workflow Designer onde as atividades geralmente são colocadas. Isso cria uma atividade de <xref:System.ServiceModel.Activities.Send> com uma opção <xref:System.Activities.Activity.DisplayName%2A> de enviar. O <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de **atividades Enviar** ou na caixa **DisplayName** da grade de propriedade.

Para criar <xref:System.ServiceModel.Activities.ReceiveReply> uma atividade e <xref:System.ServiceModel.Activities.Send> vinculá-la à atividade selecionada, clique com o botão direito do mouse no designer **de atividades Enviar,** clique no item **Criar ReceberResposta** no menu contexto e o designer **ReceiveReplyForSend** aparece abaixo do designer **Enviar.** A atividade de <xref:System.ServiceModel.Activities.ReceiveReply> é uma atividade que receberá uma mensagem como parte de um padrão de troca de solicitação/resposta de mensagem no cliente. Ele pode ser configurado com o designer **ReceiveReplyForSend.**

Alternativamente, o designer de **modelos SendAndReceiveReply** na categoria **Mensagens** da **Caixa** de <xref:System.ServiceModel.Activities.Send> Ferramentas <xref:System.ServiceModel.Activities.ReceiveReply> pode ser usado para criar um par de atividades pré-configuradas. Para obter mais informações sobre o uso dos **modelos SendAndReceiveReply** e **ReceiveReplyForSend,** consulte o tópico [EnviareReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>As propriedades de atividade de enviar

A tabela a seguir mostra as propriedades de <xref:System.ServiceModel.Activities.Send> e descreve como elas são usadas no designer. Essas propriedades podem ser editadas na grade de propriedades ou na superfície do Workflow Designer.

| Nome da propriedade | Obrigatório | Uso |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Falso | O nome amigável de atividade de <xref:System.ServiceModel.Activities.Send> . O padrão é enviar. Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | O nome da operação de serviço chamada por esta atividade de <xref:System.ServiceModel.Activities.Send> . Esta propriedade é usada para construir o valor padrão para a propriedade **Action** se a propriedade **Action** não estiver explicitamente definida. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | O nome do contrato de serviço que o serviço ser chamado implementa. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Falso | Especifica o conteúdo de mensagem ou de parâmetro para receber. Pode ser uma atividade de <xref:System.ServiceModel.Activities.ReceiveMessageContent> ou uma atividade de <xref:System.ServiceModel.Activities.ReceiveParametersContent> . Edite esta propriedade selecionando o botão ellipsis ao lado do campo **Conteúdo** na grade de propriedades ou clicando no botão **Definir...** ao lado da etiqueta **Conteúdo** na superfície do designer de **atividades Receber.** Ambos exibem a caixa de diálogo Definição de **conteúdo.** Para obter mais informações sobre como usar esta caixa, consulte o tópico [Caixa de Diálogo de Definição de Conteúdo.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Falso | Especifica <xref:System.ServiceModel.Activities.CorrelationHandle> usado para rotear a mensagem à instância apropriado de fluxo de trabalho.<br /><br /> Clique no botão elipse <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> ao lado da propriedade na grade de propriedades para abrir a caixa de diálogo **Editor** de expressão. Para obter mais informações sobre o uso desta caixa de diálogo, consulte [o tópico Como: Usar o](../workflow-designer/how-to-use-the-expression-editor.md) tópico Editor de expressão. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Falso | Especifica a coleção de objetos de <xref:System.ServiceModel.Activities.CorrelationInitializer> que inicializam vários objetos de <xref:System.ServiceModel.Activities.CorrelationHandle> que configuram esta atividade de <xref:System.ServiceModel.Activities.Send> dentro de fluxo de trabalho. Clique no botão elipse <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> ao lado da propriedade na grade de propriedades para abrir a caixa de diálogo **Adicionar iniciadores de correlação.** Para obter mais informações sobre o uso desta caixa, consulte o tópico [Caixa de diálogo Adicionar correlaçãoInicializador.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Falso | Uma coleção de tipos conhecidos para que a operação de serviço é chamada por esta atividade de <xref:System.ServiceModel.Activities.Send> . Esta propriedade deve ser usada em conjunto com a propriedade de <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> definida como <xref:System.Runtime.Serialization.DataContractSerializer>. É ignorada se <xref:System.Xml.Serialization.XmlSerializer> é usado.<br /><br /> Selecione o botão elipse ao lado do campo **KnownTypes** na grade de propriedades para exibir a caixa de diálogo **Editor de coleção de tipos** com a qual você pode adicionar tipos relevantes.<br /><br /> Selecione o botão elipse ao lado do campo **KnownTypes** na grade de propriedades para exibir a caixa de diálogo **Type Collection Editor** com a qual você pode adicionar tipos relevantes. Para obter mais informações sobre o uso desta caixa, consulte o tópico Caixa de diálogo do [editor de coleção de tipo.](../workflow-designer/type-collection-editor-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Especifica <xref:System.Net.Security.ProtectionLevel> para a mensagem.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> significa apenas autenticação.<br />2. <xref:System.Net.Security.ProtectionLevel> significa assinar dados para ajudar a garantir a integridade dos dados transmitidos.<br />3. <xref:System.Net.Security.ProtectionLevel> significa criptografar e assinar dados para ajudar a garantir a confidencialidade e integridade dos dados transmitidos. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | O serializador usar para que a operação de serviço é chamada pela atividade de <xref:System.ServiceModel.Activities.Send> . O valor padrão é <xref:System.Runtime.Serialization.DataContractSerializer>, que serializa e desserializa uma instância de um tipo em um fluxo XML ou em um documento usando um contrato fornecido de dados. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Falso | Especifica o cabeçalho da ação de mensagem. Se não for explicitamente definido, seu valor `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`é padrão para: . Se especificado em uma atividade de <xref:System.ServiceModel.Activities.Send> , a atividade de <xref:System.ServiceModel.Activities.Receive> que recebe a mensagem deve ter o mesmo valor para que a mensagem é entregada corretamente. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel> permitido o receptor de mensagem. Ele define níveis de representação de segurança, que regem o grau em que um processo de servidor pode agir em nome de um processo de cliente.<xref:System.Security.Principal.TokenImpersonationLevel>  indica que um nível da representação não é atribuído. <xref:System.Security.Principal.TokenImpersonationLevel>indica que o processo do servidor não pode obter informações de identificação sobre o cliente e não pode se passar pelo cliente. <xref:System.Security.Principal.TokenImpersonationLevel>indica que o processo do servidor pode obter informações sobre o cliente, como identificadores de segurança e privilégios, mas que ele não pode se passar pelo cliente. Isso é útil para servidores que exportam seus próprios objetos, por exemplo, os produtos de base de dados que exporte tabelas e modos de exibição. Usando informações recuperadas de cliente segurança, o servidor pode tomar decisões de acesso de validação não poderá usar outros serviços usando o contexto de segurança do cliente. <xref:System.Security.Principal.TokenImpersonationLevel>indica que o processo do servidor pode se passar pelo contexto de segurança do cliente em seu sistema local. O servidor não pode representar o cliente em sistemas remotos. <xref:System.Security.Principal.TokenImpersonationLevel>indica que o processo do servidor pode se passar pelo contexto de segurança do cliente em sistemas remotos. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | <xref:System.ServiceModel.Endpoint> que a atividade de <xref:System.ServiceModel.Activities.Send> envia à mensagem. Se esta propriedade <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> for definida, a propriedade deve ser **nula.** |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress> que a mensagem é enviada. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | O nome da configuração do ponto de extremidade. Essa propriedade é definida quando você estiver configurando um ponto de extremidade em um arquivo de configuração. Esta propriedade deve ser definida como ** \<** o nome dado no ponto final>elemento em seu arquivo de configuração. Se esta propriedade estiver <xref:System.ServiceModel.Activities.Send.Endpoint%2A> definida, a propriedade deve ser **nula.** |

## <a name="see-also"></a>Confira também

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Receber](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)