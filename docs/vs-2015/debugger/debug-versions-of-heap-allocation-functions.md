---
title: Versões de depuração das funções de alocação de Heap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 13f8d8b79ecf586048aacf3cd9442c596f184be3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691164"
---
# <a name="debug-versions-of-heap-allocation-functions"></a>Versões de depuração das funções de alocação da pilha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A biblioteca em tempo de execução C contém versões especiais de depuração das funções de alocação do heap. Essas funções têm os mesmos nomes que as versões com o _dbg anexado a elas. Este tópico descreve as diferenças entre a versão de lançamento de uma função CRT e a versão de _dbg, usando `malloc` e `_malloc_dbg` como exemplos.  
  
 Quando [Debug](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) é definido, o CRT mapeará todas [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) chama [malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Consequentemente, você não precisa reescrever seu código usando `_malloc_dbg` em vez de `malloc` para receber os benefícios durante a depuração.  
  
 No entanto, talvez você queira chamar explicitamente `_malloc_dbg`. Chamar `_malloc_dbg` explicitamente tem alguns benefícios adicionais:  
  
- Acompanhar alocações de tipo `_CLIENT_BLOCK`.  
  
- Armazenar o arquivo de origem e o número da linha em que a solicitação de alocação ocorreu.  
  
  Se você não quiser converter suas `malloc` chamadas para `_malloc_dbg`, você pode obter as informações do arquivo de origem definindo [crtdbg_map_alloc](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), que faz com que o pré-processador mapear diretamente todas as chamadas para `malloc` para `_malloc_dbg` em vez de depender de um wrapper em torno `malloc`.  
  
  Para controlar os tipos separados de alocações em blocos do cliente, você deverá chamar `_malloc_dbg` diretamente e definir o parâmetro `blockType` como `_CLIENT_BLOCK`.  
  
  Quando Debug não estiver definido, chamadas para `malloc` não serão perturbadas, as chamadas a `_malloc_dbg` são resolvidas para `malloc`, a definição de [crtdbg_map_alloc](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b) é ignorada e a fonte de informações do arquivo que pertencem à solicitação de alocação não é fornecida. Como `malloc` não tem um parâmetro de tipo de bloco, as solicitações para tipos de `_CLIENT_BLOCK` são tratadas como alocações padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)
