---
title: Relatório de ETW (Rastreamento de Eventos para Windows) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc0e139644a0b3df29109c1543140e57c5378f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838387"
---
# <a name="event-tracing-for-windows-etw-report"></a>Relatório de Rastreamento de Eventos para Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Relatório de ETW (Rastreamento de Eventos para Windows) lista os eventos ETW que são registrados em uma sessão de desempenho das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dados de ETW são coletados em um arquivo binário (.etl).  
  
> [!NOTE]
> Não é possível exibir relatórios ETW na interface [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Para obter informações sobre como coletar o ETW usando o Ferramentas de Criação de Perfil da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interface, consulte [como coletar dados do ETW (rastreamento de eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Para obter informações sobre como coletar dados ETW usando as ferramentas de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), consulte [Eventos](../profiling/events-vsperfcmd.md).  
  
- Você gera o relatório ETW usando o comando **VSReport/summary: ETW** . Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).  
  
|Column|Descrição|  
|------------|-----------------|  
|**Timestamp**|Identifica quando o evento ocorreu.|  
|**ID do Processo**|Identifica o processo que gerou o evento.|  
|**ID do thread**|Identifica o thread que gerou o evento.|  
|**Descrição**|Identifica o provedor de eventos.|  
|**Tipo**|Identifica o tipo de evento.|  
|**Propriedades**|As propriedades do evento. Cada evento é um par nome-valor separado por vírgulas e limitado entre colchetes.|
