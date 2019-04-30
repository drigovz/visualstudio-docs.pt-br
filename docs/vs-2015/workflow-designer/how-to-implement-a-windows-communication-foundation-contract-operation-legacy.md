---
title: 'Como: Implementar uma operação de contrato Windows Communication Foundation (herdado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 56866e084eac7dc3a3ac2a0b80baaa2533ccd285
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931174"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Como: Implementar uma operação do contrato do Windows Communication Foundation (herdado)
Este tópico descreve como implementar uma operação do contrato de [!INCLUDE[indigo1](../includes/indigo1-md.md)] usando o novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que direciona [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Após arrastar uma **ReceiveActivity** atividade da caixa de ferramentas para a superfície de design de fluxo de trabalho, você criará um novo [!INCLUDE[indigo2](../includes/indigo2-md.md)] de contrato ou importar um contrato existente e implementará operações. Você seleciona e/ou criar o contrato e as operações com o [escolha a caixa de diálogo da operação (herdado)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Para implementar uma operação do contrato de WCF  
  
1. Clique duas vezes o **ReceiveActivity** atividade no designer ou clique no botão de reticências próximo à **ServiceOperationInfo** propriedade no **propriedades** painel.  
  
2. Realize um dos seguintes procedimentos:  
  
   - Clique em **Adicionar contrato** no canto superior direito da caixa de diálogo. Isso criará um novo contrato e operação de [!INCLUDE[indigo2](../includes/indigo2-md.md)] para você.  
  
      - ou -  
  
   - Clique em **importação** no canto superior direito da caixa de diálogo. O [navegue e selecione uma caixa de diálogo do tipo .NET (herdado)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) é aberta. Pesquise por um assembly ou projeto que contém o contrato que você deseja. Selecione o contrato e clique em **Okey**.  
  
     Depois que um contrato é criado ou importado, você pode adicionar novos operações ao contrato criado ou importou isso. Para adicionar uma nova operação, selecione o contrato e clique em **Adicionar operação** no canto superior direito da caixa de diálogo. Quando você tiver terminado de adicionar operações, vá para a etapa 3.  
  
3. Selecione a operação que você deseja associar com a **ReceiveActivity** atividade. Você pode manipular a definição da operação alterar o nome, parâmetros, propriedades, e as configurações de permissão da operação.  
  
    Para alterar o nome, digite o novo nome na **nome da operação** caixa de texto.  
  
    Clique o **parâmetros** tab para acessar os parâmetros da operação. Você pode alterar o nome, tipo, ou a direção de um parâmetro assim como adicionar ou excluir parâmetros da operação.  
  
    Clique o **propriedades** tab para acessar a funcionalidade do exchange operação proteção com suporte e nível de mensagem da operação.  
  
    Clique o **permissões** tab para especificar quais grupos têm permissão para implementar a operação.  
  
4. Clique em **Okey** e o **ReceiveActivity** atividade exibirá o nome da operação para a operação que está implementando.  
  
5. Coloque as atividades de fluxo de trabalho que você pretende usar para a implementação da operação dentro de **ReceiveActivity** atividade.  
  
## <a name="see-also"></a>Consulte também  
 [Escolha a caixa de diálogo de operação (herdado)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Como: Invocar uma operação de contrato do Windows (legados)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Atividades de fluxo de trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)