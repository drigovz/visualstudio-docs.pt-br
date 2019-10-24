---
title: DebugBreak e __debugbreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce99cd360d75472df6326cfaf6a3f4ddb198b6d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738361"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak e __debugbreak
Você pode chamar a função DebugBreak do Win32 ou a [__debugbreak](/cpp/intrinsics/debugbreak) intrínseca em qualquer ponto em seu código. `DebugBreak` e `__debugbreak` têm o mesmo efeito de definir um ponto de interrupção nesse local.

 Como `DebugBreak` é uma chamada para uma função do sistema, os símbolos de depuração do sistema devem ser instalados para garantir que as informações corretas da pilha de chamadas sejam exibidas depois de interromper. Caso contrário, as informações da pilha de chamadas exibidas pelo depurador podem estar desativadas por um quadro. Se você usar `__debugbreak`, os símbolos não serão necessários.

## <a name="see-also"></a>Consulte também
- [Intrínsecos do compilador](/cpp/intrinsics/compiler-intrinsics)
- [Segurança do depurador](../debugger/debugger-security.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)
- [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)