---
title: Regras de uso das ferramentas de criação de perfil | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693b43d4a421bd0d0d87fbf485af88573b26adff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165725"
---
# <a name="profiling-tools-usage-rules"></a>Regras de uso das ferramentas de criação de perfil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As regras de desempenho na categoria de Uso de Ferramentas de Criação de Perfil fornecem diretrizes para usar o criador de perfil para coletar dados de forma mais eficiente.  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll está ausente](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|A criação de perfil de linha de comando pode conter dados incompletos para binários [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Isso pode ser causado por não configurar variáveis de ambiente corretas.|  
|[DA0003: Muitas amostras de kernel](../profiling/da0003-many-kernel-samples.md)|Muitas amostras de criação de perfil que ocorreram fora da execução do binário de destino foram registrados. Para coletar dados mais precisos, considere usar o método de instrumentação.|  
|[DA0004: Uso do processador elevado](../profiling/da0004-high-processor-usage.md)|Os dados de criação de perfil sugerem que seus processadores estavam consistentemente ocupados durante a criação de perfil. Para coletar dados mais precisos, considere usar o método de amostragem.|  
|[DA0008: Poucas amostras coletadas](../profiling/da0008-few-samples-collected.md)|O número de amostras coletados na criação de perfil não foi alto o suficiente para ser estatisticamente significativo. Considere realizar uma nova criação de perfil e executar o aplicativo por mais tempo. Considere também usar o método de instrumentação para coletar dados.|  
|[DA0026: Processamento de tempo de CPU do kernel excessivo](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Uma parte significativa de tempo na criação de perfil ocorreu no modo de núcleo de kernel de processador. Considere a amostragem por meio de chamadas do sistema como a métrica em vez de usar o tempo como a métrica.|  
|[DA0029: Versão de CLR sem suporte](../profiling/da0029-unsupported-clr-version.md)|O binário analisado está usando uma versão de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que não tem suporte no criador de perfil. Os relatórios do criador de perfil não podem resolver nomes de símbolos.|  
|[DA0030: Colete medidas de Interação de Camadas para projetos de banco de dados](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Foi coletado um número significativo de chamadas para métodos no namespace <xref:System.Data?displayProperty=fullName>. Para incluir dados sobre as chamadas de banco de dados, considere coletar dados de interação entre camadas em execução de análise.|
