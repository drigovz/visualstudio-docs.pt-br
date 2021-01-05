---
title: Depurar a gravação da função do gancho | Microsoft Docs
description: Leia sobre várias funções de gancho de depuração personalizadas que você pode escrever para permitir que você insira seu código em pontos predefinidos dentro do processamento normal do depurador.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: a5e2f05005d0b43d526936bfbc8018739cb1ed88
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728931"
---
# <a name="debug-hook-function-writing"></a>Gravação da função de gancho de depuração
Esta seção descreve várias funções de gancho de depuração personalizadas que você pode escrever que permitem inserir seu código em alguns pontos predefinidos no processamento normal do depurador.

## <a name="in-this-section"></a>Nesta seção
 [Funções de gancho de bloco de cliente](../debugger/client-block-hook-functions.md) Fornece orientação e um protótipo para escrever funções que validam ou relatam o conteúdo dos dados armazenados em blocos de _CLIENT_BLOCK.

 [Funções de gancho de alocação](../debugger/allocation-hook-functions.md) Define uma função de gancho de alocação, explora seus usos diferentes, indica restrições e fornece um protótipo.

 [Ganchos de alocação e alocações de memória de CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) Descreve a restrição nas funções de gancho de alocação de ignorar explicitamente `_CRT_BLOCK` os blocos se eles fizerem chamadas para as funções de biblioteca de tempo de execução C que alocam memória interna. Este tópico também listará as consequências se o gancho de alocação não ignorar os blocos de `_CRT_BLOCK` (com exemplos) e como alterar a função padrão de gancho de alocação, **CrtDefaultAllocHook**.

 [Funções do gancho de relatório](../debugger/report-hook-functions.md) Discute `_CrtSetReportHook` , que você pode usar para filtrar relatórios para se concentrar em tipos específicos de alocações. Este tópico também fornece um protótipo.

## <a name="related-sections"></a>Seções relacionadas

- [Técnicas de depuração de CRT](../debugger/crt-debugging-techniques.md) – links para técnicas de depuração para a biblioteca de Run-Time do C, incluindo o uso da biblioteca de depuração CRT, macros para relatórios, diferenças entre `malloc` e `_malloc_dbg` , gravação de funções de gancho de depuração e heap de depuração CRT.