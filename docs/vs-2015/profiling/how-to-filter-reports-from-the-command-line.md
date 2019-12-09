---
title: 'Como: Filtrar relatórios da linha de comando | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db2c9d845af962fc17da1ebd84e8dd5fe6ffadab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146009"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Como: Filtrar relatórios na linha de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao usar as opções para o comando **VSPerfReport**, você pode filtrar relatórios para um segmento de tempo específico do arquivo de dados de criação de perfil ou restringir os dados a um ou mais processos ou threads. Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opções|Descrição|  
|-------------|-----------------|  
|**StartTime:** [*Value*]|Mostrar somente dados coletados após o valor (em milésimos de segundos.)|  
|**EndTime:** [*Value*]|Mostrar apenas dados coletados antes do valor (em milésimos de segundos.)|  
|**FilterFile:** `VSPFFile`|Especifica o local de um arquivo de filtro que foi gerado da janela **Relatório de desempenho do Visual Studio**.|  
|**MsFilter:** [*StartTime,Duration*]|Mostrar somente os dados de `StartTime` até a duração de `Duration` (em milésimos de segundos).|  
|**Process:** [*Pid*]|Mostrar somente os dados do processo especificado.|  
|**Thread:** [*ThreadID*]|Mostrar somente os dados do thread especificado.|  
|**Thread:** [*ThreadID,ProcessID*]|Mostrar somente os dados do thread especificado associados ao processo especificado.|
