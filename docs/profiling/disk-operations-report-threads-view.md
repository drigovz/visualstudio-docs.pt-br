---
title: Relatório de operações de disco (exibição de threads) | Microsoft Docs
description: O relatório de operações de disco mostra operações de E/S de disco em canais de disco. Veja quais informações são relatadas para cada acesso ao disco.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6b0e15257d67e1d7ff1aaef14c2ebfff3775d6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923729"
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

## <a name="see-also"></a>Confira também
- [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)