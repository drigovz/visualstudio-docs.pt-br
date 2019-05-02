---
title: Relatório de operações de disco (exibição de threads) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69cbef53bcca74cceba4f9409b578fca45a58806
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970064"
---
# <a name="disk-operations-report-threads-view"></a>Relatório de operações de disco (exibição de threads)
O relatório de operações de disco mostra operações de E/S de disco em canais de disco.

 Para cada acesso ao disco que ocorre em nome do processo que está sendo atribuído na janela de tempo visível no momento, essas informações são relatadas:

- O nome e o PID do processo que executou o acesso ao disco

- A ID do thread que acessou o disco

- O nome do arquivo que foi acessado

- O número de leituras por arquivo

- O número de bytes lidos

- A latência de leitura, em milissegundos

- O número de gravações

- O número de bytes gravados

- A latência de gravação, em milissegundos

## <a name="see-also"></a>Consulte também
- [Exibição de Threads](../profiling/threads-view-parallel-performance.md)