---
title: Exibições de fluxo de trabalho Sequencial (Herdado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 859fa44b44a295dc3e9f27fc168092a9fe2beebf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292357"
---
# <a name="sequential-workflow-views-legacy"></a>Exibições sequenciais de fluxo de trabalho (legados)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] fornece [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado que pode ser usado para direcionar [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 ph x="1" /&gt; fornece uma maneira de criar aplicativos graficamente de [!INCLUDE[wfd2](../includes/wfd2-md.md)] usando a interface do usuário e de [!INCLUDE[wf](../includes/wf-md.md)] . aplicativos de[!INCLUDE[wf](../includes/wf-md.md)] são compostos das etapas do processo de fluxo de trabalho chamadas atividades. Para criar um fluxo de trabalho, compor atividades na superfície de design arrastando seus respectivos designer de atividade de **Caixa de Ferramentas** na superfície de design.

 Quando você cria um fluxo de trabalho Sequencial, que é um [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040), três exibições do fluxo de trabalho estão disponíveis. Esses modos de exibição são acessíveis a partir do menu **Fluxo de Trabalho** e do menu de contexto na superfície de design.

 A tabela a seguir lista o nome e a descrição de cada uma.

|Opção de menu/guia|Descrição|
|----------------------|-----------------|
|**Exibir SequentialWorkflow**|Clique com o botão direito do mouse na superfície de design e selecione a opção de **Exibição SequentialWorkflow** do menu de contexto exibir o modo de **Fluxo de Trabalho Sequencial** , que mostra a representação gráfica atividades base de fluxo de trabalho sequencial. Ou **Exibir SequentialWorkflow** partir do menu de **Fluxo de Trabalho** .|
|**Exibir manipulador de cancelamento**|Clique com o botão direito do mouse na superfície de design e selecione a opção **Exibir manipulador de cancelamento** no menu de contexto para exibir o modo de exibição de **fluxo de trabalho Sequencial** , que mostra a atividade [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) associada ao fluxo de trabalho. Ou **Exibir Manipulador de Cancelamento** partir do menu de **Fluxo de Trabalho** .|
|**Exibir manipulador de falhas**|Clique com o botão direito do mouse na superfície de design e selecione a opção **Exibir manipulador de falhas** no menu de contexto para exibir a exibição **falhas** , que mostra a atividade [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) associada ao fluxo de trabalho. Ou **Exibir o manipulador de falha** partir do menu de **Fluxo de Trabalho** .|

 Para obter mais informações sobre modos de exibição semelhantes, consulte [exibições de atividade (Herdado)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Consulte também
 [Exibições de atividade (herdadas)](../workflow-designer/activity-views-legacy.md) [criando modos de fluxo de trabalho herdados](../workflow-designer/creating-legacy-workflow-projects.md) [modelos de criação](https://go.microsoft.com/fwlink?LinkID=65014)