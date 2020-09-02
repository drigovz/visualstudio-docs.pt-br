---
title: Como filtrar relatórios da linha de comando | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146009"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>Como filtrar relatórios a partir da linha de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao usar as opções para o comando **VSPerfReport**, você pode filtrar relatórios para um segmento de tempo específico do arquivo de dados de criação de perfil ou restringir os dados a um ou mais processos ou threads. Para obter mais informações sobre esse comando, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opções|Descrição|  
|-------------|-----------------|  
|**StartTime:**[*valor*]|Mostrar apenas os dados coletados depois do valor (em milissegundos).|  
|**EndTime:**[*valor*]|Mostrar apenas os dados coletados antes do valor (em milissegundos).|  
|**FilterFile:** `VSPFFile`|Especifica o local de um arquivo de filtro que foi gerado na janela **relatório de desempenho do Visual Studio** .|  
|**MsFilter:**[*tempo de início, duração*]|Mostrar apenas os dados de `StartTime` até a duração de `Duration` (em milissegundos).|  
|**Processo:**[*pid*]|Mostrar somente os dados do processo especificado.|  
|**Thread:**[*ThreadID*]|Mostra apenas os dados do thread especificado.|  
|**Thread:**[*ThreadID, ProcessId*]|Mostrar somente os dados do thread especificado associados ao processo especificado.|
