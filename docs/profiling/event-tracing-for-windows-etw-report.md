---
title: Relatório de ETW (Rastreamento de Eventos para Windows) | Microsoft Docs
description: Leia sobre o relatório ETW (rastreamento de eventos para Windows), que lista os eventos ETW que foram registrados em uma sessão de desempenho do Visual Studio Ferramentas de Criação de Perfil.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1a5a962ba3eaeee2c9f1e26132bf4ce6b12d9347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955288"
---
# <a name="event-tracing-for-windows-etw-report"></a>Relatório do ETW (Rastreamento de Eventos para Windows)
O Relatório de ETW (Rastreamento de Eventos para Windows) lista os eventos ETW que são registrados em uma sessão de desempenho das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Os dados ETW são coletados em um binário (.*ETL*).

> [!NOTE]
> Não é possível exibir relatórios ETW na interface [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Para obter informações sobre como coletar dados do ETW usando as Ferramentas de Criação de Perfil na interface do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], confira [Como coletar dados do ETW (Rastreamento de Eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Para obter informações sobre como coletar dados ETW usando as ferramentas de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), consulte [Eventos](../profiling/events-vsperfcmd.md).

- Você gera o relatório ETW usando o comando **VSReport/summary: ETW** . Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).

|Coluna|Descrição|
|------------|-----------------|
|**Timestamp**|Identifica quando o evento ocorreu.|
|**ID do Processo**|Identifica o processo que gerou o evento.|
|**ID do thread**|Identifica o thread que gerou o evento.|
|**Descrição**|Identifica o provedor de eventos.|
|**Tipo**|Identifica o tipo de evento.|
|**Propriedades**|As propriedades do evento. Cada evento é um par nome-valor separado por vírgulas e limitado entre colchetes.|
