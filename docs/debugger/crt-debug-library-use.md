---
title: Uso da biblioteca de depuração CRT | Microsoft Docs
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20aeee220bec600c2232286d18600b04201ad03b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745617"
---
# <a name="crt-debug-library-use"></a>Uso da biblioteca de depuração CRT
A biblioteca em tempo de execução C fornece amplo suporte à depuração. Para usar uma das bibliotecas de depuração do CRT, você deve vincular com [/debug](/cpp/build/reference/debug-generate-debug-info) e compilar com **/MDD**, **/MTD**ou **/ldd**.

## <a name="remarks"></a>Comentários
 As definições e macros principais de depuração de CRT podem ser encontradas no arquivo de cabeçalho CRTDBG.h.

 As funções nas bibliotecas de depuração de CRT são criadas com informações de depuração ([/Z7, /Zd, /Zi, /ZI (formato das informações de depuração)](/cpp/build/reference/z7-zi-zi-debug-information-format)) e sem otimização. Algumas funções contêm asserções para verificar os parâmetros passados a elas, e o código-fonte será fornecido. Com esse código-fonte, você pode acessar funções de CRT para confirmar se as funções estão funcionando conforme o esperado e verificar se há parâmetros incorretos ou estados de memória. (Qualquer tecnologia de CRT é proprietária e não fornece código-fonte para tratamento de exceções, ponto flutuante e algumas outras rotinas.)

 Para obter mais informações sobre as várias bibliotecas em tempo de execução que você pode usar, confira [Bibliotecas em tempo de execução C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Confira também

- [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)
- [/MD,/MT,/LD (use a biblioteca de tempo de execução)](/cpp/build/reference/md-mt-ld-use-run-time-library)