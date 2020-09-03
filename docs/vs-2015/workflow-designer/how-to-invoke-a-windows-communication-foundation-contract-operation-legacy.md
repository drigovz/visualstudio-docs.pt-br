---
title: Como invocar uma operação de contrato de Windows Communication Foundation (Herdado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603701"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Como: Chamar uma operação do Windows Communication Foundation (o legados)
Este tópico descreve como chamar uma operação do contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Depois de arrastar uma atividade **SendActivity** da caixa de ferramentas para a superfície de design do fluxo de trabalho, você deve importar um contrato existente e determinar qual operação será invocada dessa atividade **SendActivity** . Você seleciona seu contrato e suas operações por meio da [caixa de diálogo escolher operação (herdada)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Além disso, se você estiver usando um arquivo de configuração com o serviço, você precisará especificar <xref:System.Workflow.Activities.ChannelToken>. <xref:System.Workflow.Activities.ChannelToken> identifica a configuração do ponto de extremidade a atividade de enviar usará para se conectar ao serviço de fluxo de trabalho.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>Para chamar a reduzir a operação de uma atividade de SendActivity

1. Clique duas vezes na atividade **SendActivity** no designer ou clique nas reticências ao lado da propriedade **ServiceOperationInfo** no painel **Propriedades** .

2. Quando a caixa de diálogo **escolher operação** for aberta, clique em **importar** no canto superior direito da caixa de diálogo.

     A [caixa de diálogo Procurar e selecionar um tipo do .net (Herdado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) é aberta.

3. Pesquise por um assembly ou projeto que contém o contrato que você deseja.

4. Selecione o contrato e clique em **OK**.

5. Em **operações disponíveis**, selecione a operação que você deseja invocar e clique em **OK**.

### <a name="to-specify-a-channel-token"></a>Para especificar um token de canal

1. Selecione a atividade de <xref:System.Workflow.Activities.SendActivity> no designer.

2. No painel **Propriedades** , especifique um nome para o <xref:System.Workflow.Activities.ChannelToken> . Este nome identifica unicamente o símbolo do canal.

3. Expanda o nó simbólico do canal e especifique um nome para o ponto final de cliente que você usará no campo de <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A> . A configuração de ponto de extremidade de mesmo nome no arquivo de configuração será usada para configurar o canal.

4. Crie a configuração de ponto de extremidade no arquivo de configuração, se ele não existir. Para obter mais informações sobre como configurar seu cliente, consulte [visão geral do cliente WCF](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).

## <a name="see-also"></a>Consulte Também
 [Caixa de diálogo escolher operação (herdada)](../workflow-designer/choose-operation-dialog-box-legacy.md) [como implementar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)