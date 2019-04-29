---
title: Gravação da função de gancho de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], CRT debug support
- debug hook functions
- hooks, debug
- hooks
- debugging [CRT], debug hook functions
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82145d39adc519bfd1324cc36805cea7b97b1664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563367"
---
# <a name="debug-hook-function-writing"></a>Gravação da função de gancho de depuração
Esta seção descreve várias funções de gancho de depuração personalizadas que você pode escrever que permitem inserir seu código em alguns pontos predefinidos no processamento normal do depurador.

## <a name="in-this-section"></a>Nesta seção
 [Funções de gancho de bloco de cliente](../debugger/client-block-hook-functions.md) fornece orientação e um protótipo para escrever funções que validam ou reportam o conteúdo dos dados armazenados em blocos client_block.

 [Funções de gancho de alocação](../debugger/allocation-hook-functions.md) define uma função de gancho de alocação, explora seus usos diferentes, destaca as restrições e fornece um protótipo.

 [Ganchos de alocação e alocações de memória do CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) descreve a limitação de funções de gancho de alocação de Ignorar explicitamente `_CRT_BLOCK` bloqueia se eles fizerem chamadas às funções de biblioteca de tempo de execução C que alocam memória interna. Este tópico também listará as consequências se o gancho de alocação não ignorar os blocos de `_CRT_BLOCK` (com exemplos) e como alterar a função padrão de gancho de alocação, **CrtDefaultAllocHook**.

 [Funções de gancho de relatório](../debugger/report-hook-functions.md) aborda `_CrtSetReportHook`, que você pode usar para filtrar relatórios para se concentrar em tipos específicos de alocações. Este tópico também fornece um protótipo.

## <a name="related-sections"></a>Seções relacionadas

- [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md) -Links para técnicas de depuração para a biblioteca de tempo de execução C, incluindo o uso da biblioteca de depuração do CRT, macros para relatórios, as diferenças entre `malloc` e `_malloc_dbg`, escrevendo funções de gancho de depuração e CRT heap de depuração.