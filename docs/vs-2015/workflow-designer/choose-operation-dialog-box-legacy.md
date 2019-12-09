---
title: Caixa de diálogo escolher operação (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659169"
---
# <a name="choose-operation-dialog-box-legacy"></a>Escolha a caixa de diálogo da operação (o legados)
Este tópico descreve como usar a caixa de diálogo **escolher operação** no [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 A caixa de diálogo **escolher operação** é usada para selecionar uma operação a ser associada a uma atividade de <xref:System.Workflow.Activities.ReceiveActivity> ou uma atividade de <xref:System.Workflow.Activities.SendActivity>. Para obter mais informações sobre como usar essa caixa de diálogo com essas atividades, consulte [como implementar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) e [como invocar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).

 A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo **escolher operação** .

|Elemento da Interface do Usuário|Descrição|
|----------------|-----------------|
|**Adicionar contrato**|Cria um novo contrato para você. Você pode definir novos operações no contrato. (Isso é usado com <xref:System.Workflow.Activities.ReceiveActivity> somente.)|
|**Adicionar operação**|Adiciona novas operações a um novo contrato que você criou na caixa de diálogo **escolher operação** . **Observação:**  Você pode adicionar novas operações somente aos contratos criados por meio da caixa de diálogo **escolher operação** . <br /><br /> (Isso é usado com <xref:System.Workflow.Activities.ReceiveActivity> somente.)|
|**Importar...**|Importa um contrato definido anteriormente e permite que você selecione uma operação do contrato.|
|**Nome da operação**|Nome da operação selecionada. Essa caixa de texto estará disponível para edição somente se você tiver criado uma operação por meio da caixa de diálogo **escolher operação** .|
|**Parâmetros**|Catalogue para conter as definições de parâmetro para a operação selecionada. **Observação:**  As definições de parâmetros só poderão ser alteradas se você tiver criado uma operação por meio da caixa de diálogo **escolher operação** .|
|**Propriedades**|Catalogue para conter configurações de <xref:System.Net.Security.ProtectionLevel> para as mensagens enviadas entre o cliente e o serviço. **Observação:**  Essa guia só será habilitada se você tiver criado uma operação por meio da caixa de diálogo **escolher operação** .|
|**Permissões**|Catalogue para conter propriedades de <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> e de <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> de usuários são permitidos que chamar a operação. Por exemplo, se apenas os usuários do grupo Administradores tiverem permissão para chamar essa operação, você escreveria "administradores" na caixa de texto **função** .<br /><br /> Essa guia é habilitada para ambas as operações criadas por meio da caixa de diálogo **ChooseOperation** e operações que foram importadas por meio do botão **importar** .|

> [!NOTE]
> A caixa de diálogo **escolher operação** mostra somente contratos ou operações que são usados por outras atividades de <xref:System.Workflow.Activities.SendActivity> no fluxo de trabalho. Da mesma forma, a caixa de diálogo **escolher operação** para <xref:System.Workflow.Activities.ReceiveActivity> atividades mostra apenas contratos ou operações que são usadas por outras atividades **ReceiveActivity** no fluxo de trabalho.

## <a name="see-also"></a>Consulte também
 [Como: implementar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [como invocar uma operação de contrato do WCF (Herdado)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Designer herdado para ajuda da interface do usuário do Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)