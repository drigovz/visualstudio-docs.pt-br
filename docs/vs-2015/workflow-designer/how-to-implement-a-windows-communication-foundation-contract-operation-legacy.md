---
title: Como implementar uma operação de contrato de Windows Communication Foundation (Herdado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603874"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Como: Implementar uma operação do Windows Communication Foundation (o legados)
Este tópico descreve como implementar uma operação do contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Depois de arrastar uma atividade **ReceiveActivity** da caixa de ferramentas para a superfície de design do fluxo de trabalho, você criará um novo [!INCLUDE[indigo2](../includes/indigo2-md.md)] contrato ou importará um contrato existente e implementará as operações. Você seleciona e/ou cria seu contrato e suas operações por meio da [caixa de diálogo escolher operação (herdada)](../workflow-designer/choose-operation-dialog-box-legacy.md).

### <a name="to-implement-a-wcf-contract-operation"></a>Para implementar uma operação do contrato de WCF

1. Clique duas vezes na atividade **ReceiveActivity** no designer ou clique nas reticências ao lado da propriedade **ServiceOperationInfo** no painel **Propriedades** .

2. Realize um dos seguintes procedimentos:

   - Clique em **Adicionar contrato** no canto superior direito da caixa de diálogo. Isso criará um novo contrato e operação de [!INCLUDE[indigo2](../includes/indigo2-md.md)] para você.

      - ou -

   - Clique em **importar** no canto superior direito da caixa de diálogo. A [caixa de diálogo Procurar e selecionar um tipo do .net (Herdado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) é aberta. Pesquise por um assembly ou projeto que contém o contrato que você deseja. Selecione o contrato e clique em **OK**.

     Depois que um contrato é criado ou importado, você pode adicionar novos operações ao contrato criado ou importou isso. Para adicionar uma nova operação, selecione o contrato e clique em **Adicionar operação** no canto superior direito da caixa de diálogo. Quando você tiver terminado de adicionar operações, vá para a etapa 3.

3. Selecione a operação que você deseja associar à atividade **ReceiveActivity** . Você pode manipular a definição da operação alterar o nome, parâmetros, propriedades, e as configurações de permissão da operação.

    Para alterar o nome, digite o novo nome na caixa de texto **nome da operação** .

    Clique na guia **parâmetros** para acessar os parâmetros da operação. Você pode alterar o nome, tipo, ou a direção de um parâmetro assim como adicionar ou excluir parâmetros da operação.

    Clique na guia **Propriedades** para acessar o nível de proteção da operação e a funcionalidade de troca de mensagens com suporte da operação.

    Clique na guia **permissões** para especificar quais grupos têm permissão para implementar a operação.

4. Clique em **OK** e a atividade **ReceiveActivity** exibirá o nome da operação para a operação que está sendo implementada.

5. Coloque as atividades de fluxo de trabalho que você pretende usar para a implementação dessa operação dentro da atividade **ReceiveActivity** .

## <a name="see-also"></a>Consulte Também
 [Caixa de diálogo escolher operação (herdada)](../workflow-designer/choose-operation-dialog-box-legacy.md) [como invocar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)