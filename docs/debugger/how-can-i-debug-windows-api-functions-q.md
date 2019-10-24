---
title: Depurar funções da API do Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.api
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], Windows API functions
- NT symbols and debugging Windows API functions
- Windows API functions, debugging
- Windows API, debugging API functions
- APIs, debugging
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7b5f3842160f4ffc6cecd41e65dd05ab7566dd0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734358"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Como depurar funções de API do Windows?
Se você desejar depurar uma função de API do Windows que tenha os símbolos do NT carregados, deverá fazer o seguinte.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Para definir um ponto de interrupção em uma função de API do Windows com os símbolos do NT carregados

- Digite o nome da função junto com o nome da DLL em que a função reside. No código de 32 bits, use a forma decorada do nome da função. Para definir um ponto de interrupção em **MessageBeep**, por exemplo, você precisa inserir o seguinte.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Para obter o nome decorado, consulte [exibindo nomes decorados](https://msdn.microsoft.com/library/f79e2717-a4db-4d12-a689-69830cce2be0).

## <a name="see-also"></a>Consulte também
- [Perguntas frequentes de depuração de código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)
