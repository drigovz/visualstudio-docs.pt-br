---
title: Exibições de atividade (herdadas) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7d8a13890814b56865200acf95c8e0565b52b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655218"
---
# <a name="activity-views-legacy"></a>Visualizações de atividade (legados)
Muitas das atividades fornecidas por [!INCLUDE[wf](../includes/wf-md.md)], que fluxos de trabalho são compostos, têm várias exibições de design disponíveis em [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Quando você arrasta um designer de atividade da **caixa de ferramentas** para a superfície de design e, depois, sempre que seleciona a atividade, você pode alternar entre os diferentes modos de exibição de design usando o menu de **fluxo de trabalho** ou clicando com o botão direito do mouse no selecionado actividade. Além disso, quando você move o ponteiro sobre o nome de uma atividade selecionada, um conjunto lista suspensa de guias que aparece você pode usar para alternar entre modos de exibição diferentes.

 Cada atividade tem pelo menos uma exibição; Essa é a exibição padrão mostrada quando você arrasta um designer de atividade da **caixa de ferramentas** para a superfície de design. Essa exibição padrão de atividade está disponível como a opção de **exibição [tipo de atividade]** nos menus e na guia, por exemplo, **Exibir paralelo**. A maioria das atividades têm modos de exibição adicionais e as atividades diferentes podem ter diferentes modos de exibição. Por exemplo, a atividade [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) tem a exibição de compensação e a atividade [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) tem uma exibição de eventos. Muitas das atividades fornecidas com Windows Workflow Foundation têm o **manipulador de exibição cancelar** e exibem exibições de design de **falhas** para exibir o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) e um [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associado a eles.

 A tabela a seguir lista o nome e a descrição de cada uma.

|Opção de menu/guia|Descrição|
|----------------------|-----------------|
|**View [tipo de atividade]**|Selecione este menu catalogue ou a opção para exibir a representação gráfica padrão de atividade selecionada.|
|**Exibir manipulador de cancelamento**|Selecione esta exibição de opção de menu ou guia para exibir o [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associado à atividade selecionada.|
|**Exibir manipulador de falhas**|Selecione esta exibição de opção de menu ou guia para exibir o [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associado à atividade selecionada.|
|**Exibir manipulador de compensação**|Selecione esta exibição de opção de menu ou guia para exibir o [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associado à [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)selecionada.|
|**Exibir manipulador de eventos**|Selecione esta exibição de opção de menu ou guia para exibir o [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associado ao [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)selecionado.|

 Para obter informações sobre modos de exibição semelhantes, consulte [exibições de fluxo de trabalho Sequencial (Herdado)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Consulte também
 [Exibições de fluxo de trabalho sequenciais de atividades de fluxo de](../workflow-designer/sequential-workflow-views-legacy.md) [trabalho herdadas](../workflow-designer/legacy-workflow-activities.md)