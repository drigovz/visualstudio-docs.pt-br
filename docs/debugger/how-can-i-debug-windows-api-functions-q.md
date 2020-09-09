---
title: Depurar funções da API do Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 06/03/2020
ms.topic: how-to
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
ms.openlocfilehash: 3f7b293270facbbfa0d2174121ff6a3ac736b75a
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599886"
---
# <a name="how-can-i-debug-windows-api-functions"></a>Como depurar funções de API do Windows?
Se você desejar depurar uma função de API do Windows que tenha os símbolos do NT carregados, deverá fazer o seguinte.

### <a name="to-set-a-breakpoint-on-a-windows-api-function-with-nt-symbols-loaded"></a>Para definir um ponto de interrupção em uma função de API do Windows com os símbolos do NT carregados

- No [ponto de interrupção da função](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file), insira o nome da função junto com o nome da dll na qual a função reside (consulte o operador de [contexto](../debugger/context-operator-cpp.md)). No código de 32 bits, use a forma decorada do nome da função. Para definir um ponto de interrupção em **MessageBeep**, por exemplo, você precisa inserir o seguinte.

    ```cpp
    {,,USER32.DLL}_MessageBeep@4
    ```

     Para obter o nome decorado, consulte [exibindo nomes decorados](/previous-versions/5x49w699(v=vs.140)).

     Você pode testar o nome decorado e exibi-lo no código de desmontagem. Enquanto estiver em pausa na função no depurador do Visual Studio, clique com o botão direito do mouse na função no editor de código ou na janela pilha de chamadas e escolha **ir para desmontagem**.

- No código de 64 bits, você pode usar o nome não decorado.

    ```cpp
    {,,USER32.DLL}MessageBeep
    ```

## <a name="see-also"></a>Confira também
- [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)