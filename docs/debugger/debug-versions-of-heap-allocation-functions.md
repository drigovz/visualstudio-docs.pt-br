---
title: Versões de depuração das funções de alocação de Heap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- debugging [CRT], heap allocation functions
- debugging memory leaks, CRT debug library functions
- malloc function
- memory leaks, CRT debug library functions
- heap allocation, debug
- _malloc_dbg function
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7df6a0ebc161d794a39e9e16b3b73abe42c6ec7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53862403"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versões de depuração das funções de alocação da pilha
A biblioteca em tempo de execução C contém versões especiais de depuração das funções de alocação do heap. Essas funções têm os mesmos nomes que as versões com o _dbg anexado a elas. Este tópico descreve as diferenças entre a versão de lançamento de uma função CRT e a versão de _dbg, usando `malloc` e `_malloc_dbg` como exemplos.  
  
 Quando [Debug](/cpp/c-runtime-library/debug) é definido, o CRT mapeará todas [malloc](/cpp/c-runtime-library/reference/malloc) chama [malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Consequentemente, você não precisa reescrever seu código usando `_malloc_dbg` em vez de `malloc` para receber os benefícios durante a depuração.  
  
 No entanto, talvez você queira chamar explicitamente `_malloc_dbg`. Chamar `_malloc_dbg` explicitamente tem alguns benefícios adicionais:  
  
- Acompanhar alocações de tipo `_CLIENT_BLOCK`.  
  
- Armazenar o arquivo de origem e o número da linha em que a solicitação de alocação ocorreu.  
  
  Se você não quiser converter suas `malloc` chamadas para `_malloc_dbg`, você pode obter as informações do arquivo de origem definindo [crtdbg_map_alloc](/cpp/c-runtime-library/crtdbg-map-alloc), que faz com que o pré-processador mapear diretamente todas as chamadas para `malloc` para `_malloc_dbg` em vez de depender de um wrapper em torno `malloc`.  
  
  Para controlar os tipos separados de alocações em blocos do cliente, você deverá chamar `_malloc_dbg` diretamente e definir o parâmetro `blockType` como `_CLIENT_BLOCK`.  
  
  Quando Debug não estiver definido, chamadas para `malloc` não serão perturbadas, as chamadas a `_malloc_dbg` são resolvidas para `malloc`, a definição de [crtdbg_map_alloc](/cpp/c-runtime-library/crtdbg-map-alloc) é ignorada e a fonte de informações do arquivo que pertencem à solicitação de alocação não é fornecida. Como `malloc` não tem um parâmetro de tipo de bloco, as solicitações para tipos de `_CLIENT_BLOCK` são tratadas como alocações padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)