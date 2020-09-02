---
title: Funções de gancho de bloco de cliente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702332"
---
# <a name="client-block-hook-functions"></a>Funções de gancho do bloco de clientes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você quiser validar ou reportar o conteúdo dos dados armazenados em blocos `_CLIENT_BLOCK`, poderá escrever uma função especificamente para essa finalidade. A função que você escreve deverá ter um protótipo semelhante ao seguinte, conforme definido em CRTDBG.H:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Em outras palavras, sua função de gancho deve aceitar um ponteiro **void** para o início do bloco de alocação, junto com um valor do tipo **size_t** que indica o tamanho da alocação e retornar `void`. Além disso, o conteúdo depende de você.  
  
 Quando você tiver instalado a função de gancho usando [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), ela será chamada sempre que um bloco `_CLIENT_BLOCK` for despejado. Você pode usar [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) para obter informações sobre o tipo ou subtipo de blocos despejados.  
  
 O ponteiro para sua função que você passa para `_CrtSetDumpClient` é do tipo **_CRT_DUMP_CLIENT**, conforme definido em CRTDBG.H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar a gravação da função do gancho](../debugger/debug-hook-function-writing.md)   
 [Exemplo de crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
