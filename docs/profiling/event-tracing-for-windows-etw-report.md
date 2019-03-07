---
title: Relatório de ETW (Rastreamento de Eventos para Windows) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf64c2fae940de74978fb2d6c10ce380ed3958d5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630178"
---
# <a name="event-tracing-for-windows-etw-report"></a>Relatório do ETW (Rastreamento de Eventos para Windows)
O Relatório de ETW (Rastreamento de Eventos para Windows) lista os eventos ETW que são registrados em uma sessão de desempenho das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os dados do ETW são coletados em um arquivo binário (.*etl*).

> [!NOTE]
>  Não é possível exibir relatórios ETW na interface [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Para obter informações sobre como coletar dados do ETW usando as Ferramentas de Criação de Perfil na interface do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], veja [Como: Coletar dados do ETW (Rastreamento de Eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Para obter informações sobre como coletar dados ETW usando as ferramentas de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), consulte [Eventos](../profiling/events-vsperfcmd.md).

- O relatório de ETW é gerado usando o comando **VSReport/Summary:ETW**. Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).

|Column|Descrição|
|------------|-----------------|
|**Carimbo de data/hora**|Identifica quando o evento ocorreu.|
|**ID do Processo**|Identifica o processo que gerou o evento.|
|**ID do Thread**|Identifica o thread que gerou o evento.|
|**Descrição**|Identifica o provedor de eventos.|
|**Tipo**|Identifica o tipo de evento.|
|**Propriedades**|As propriedades do evento. Cada evento é um par nome-valor separado por vírgulas e limitado entre colchetes.|