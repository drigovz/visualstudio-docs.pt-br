---
title: Localizar falha de chamada ao chamar uma função muitas vezes
description: Consulte uma técnica para definir um ponto de interrupção em uma função de modo que a interrupção ocorra apenas na chamada para a qual a função falha.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8937b58277450198d7c0927d93118c492faedfbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883877"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Durante a chamada de uma função centenas de vezes, como sei qual chamada falhou?
## <a name="problem-description"></a>Descrição do problema
 Meu programa falha em uma chamada para uma determinada função, `CnvtV`. O programa provavelmente chama essa função algumas centenas de vezes antes de falhar. Se eu definir um ponto de interrupção de local em `CnvtV`, o programa parará em cada chamada a essa função, e eu não quero isso. Eu não sei quais condições causam a falha na chamada, portanto, não consigo definir um ponto de interrupção condicional. O que posso fazer?

## <a name="solution"></a>Solução
 Você pode definir um ponto de interrupção na função com o campo **Contagem de Ocorrências** para um valor mais alto que nunca será atingido. Nesse caso, como você acredita que a função `CnvtV` será chamada algumas centenas de vezes, defina a **Contagem de Ocorrências** como 1000 ou mais. Execute o programa e aguarde a chamada falhar. Quando falhar, abra a janela Pontos de Interrupção e verifique a lista de pontos de interrupção. O ponto de interrupção definido em `CnvtV` aparece, seguido pela contagem de ocorrências e o número de iterações restantes:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Agora você sabe que a função falha na 101a chamada. Se você redefinir o ponto de interrupção com uma contagem de ocorrências de 101 e executar o programa novamente, o programa de chamada parará na chamada para `CnvtV` que causou a falha.

## <a name="see-also"></a>Confira também
- [Perguntas frequentes sobre depuração de código nativo](../debugger/debugging-native-code-faqs.md)
- [Configuração dos pontos de interrupção](/previous-versions/ktf38f66(v=vs.100))
- [Depurando código nativo](../debugger/debugging-native-code.md)