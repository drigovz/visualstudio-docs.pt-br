---
title: Como filtrar relatórios da linha de comando | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a93e1bb2e1d3a65d82a4a0ac54e903ee20553d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290141"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Como filtrar relatórios a partir da linha de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao usar as opções para o comando **VSPerfReport**, você pode filtrar relatórios para um segmento de tempo específico do arquivo de dados de criação de perfil ou restringir os dados a um ou mais processos ou threads. Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opções|Descrição|  
|-------------|-----------------|  
|**StartTime:**[*Value*]|Mostrar somente dados coletados após o valor (em milésimos de segundos.)|  
|**EndTime:**[*Value*]|Mostrar apenas dados coletados antes do valor (em milésimos de segundos.)|  
|**FilterFile:** `VSPFFile`|Especifica o local de um arquivo de filtro que foi gerado da janela **Relatório de desempenho do Visual Studio**.|  
|**MsFilter:**[*StartTime,Duration*]|Mostrar somente os dados de `StartTime` até a duração de `Duration` (em milésimos de segundos).|  
|**Process:**[*Pid*]|Mostrar somente os dados do processo especificado.|  
|**Thread:**[*ThreadID*]|Mostrar somente os dados do thread especificado.|  
|**Thread:**[*ThreadID,ProcessID*]|Mostrar somente os dados do thread especificado associados ao processo especificado.|



