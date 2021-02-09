---
title: Funções de gancho de bloco de cliente | Microsoft Docs
description: Escreva uma função de gancho de bloco de cliente para validar ou relatar o conteúdo dos dados armazenados em blocos de _CLIENT_BLOCK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0378f2260a9bf71cf7ac1192b7eb7a2259d8ace2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865872"
---
# <a name="client-block-hook-functions"></a>Funções de gancho do bloco de clientes
Se você quiser validar ou reportar o conteúdo dos dados armazenados em blocos `_CLIENT_BLOCK`, poderá escrever uma função especificamente para essa finalidade. A função que você escreve deverá ter um protótipo semelhante ao seguinte, conforme definido em CRTDBG.H:

```cpp
void YourClientDump(void *, size_t)
```

 Em outras palavras, sua função de gancho deve aceitar um ponteiro **void** para o início do bloco de alocação, junto com um valor do tipo **size_t** que indica o tamanho da alocação e retornar `void`. Além disso, o conteúdo depende de você.

 Quando você tiver instalado a função de gancho usando [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), ela será chamada sempre que um bloco `_CLIENT_BLOCK` for despejado. Você pode usar [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) para obter informações sobre o tipo ou subtipo de blocos despejados.

 O ponteiro para sua função que você passa para `_CrtSetDumpClient` é do tipo **_CRT_DUMP_CLIENT**, conforme definido em CRTDBG.H:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Confira também

- [Depurar a gravação da função do gancho](../debugger/debug-hook-function-writing.md)
- [Amostra de crt_dbg2](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)