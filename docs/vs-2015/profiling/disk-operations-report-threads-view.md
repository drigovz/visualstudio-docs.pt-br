---
title: Relatório de operações de disco (exibição de threads) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f121b8939ff55c9274cd04560ae7d507e22fde5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245148"
---
# <a name="disk-operations-report-threads-view"></a>Relatório de operações de disco (exibição de threads)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O relatório de operações de disco mostra operações de E/S de disco em canais de disco.  
  
 Para cada acesso ao disco que ocorre em nome do processo que está sendo atribuído na janela de tempo visível no momento, essas informações são relatadas:  
  
-   O nome e o PID do processo que executou o acesso ao disco  
  
-   A ID do thread que acessou o disco  
  
-   O nome do arquivo que foi acessado  
  
-   O número de leituras por arquivo  
  
-   O número de bytes lidos  
  
-   A latência de leitura, em milissegundos  
  
-   O número de gravações  
  
-   O número de bytes gravados  
  
-   A latência de gravação, em milissegundos  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)



