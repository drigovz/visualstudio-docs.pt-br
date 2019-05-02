---
title: DebugBreak e debugbreak | Microsoft Docs
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
ms.openlocfilehash: b6c4b9d780caf7589eecdc709cbede577dd7a6fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852704"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak e __debugbreak
Você pode chamar a função DebugBreak do Win32 ou a [__debugbreak](/cpp/intrinsics/debugbreak) intrínseca em qualquer ponto em seu código. `DebugBreak` e `__debugbreak` têm o mesmo efeito de definir um ponto de interrupção nesse local.

 Como `DebugBreak` é uma chamada para uma função do sistema, os símbolos de depuração do sistema devem ser instalados para garantir que as informações corretas da pilha de chamadas sejam exibidas depois de interromper. Caso contrário, as informações da pilha de chamadas exibidas pelo depurador podem estar desativadas por um quadro. Se você usar `__debugbreak`, os símbolos não serão necessários.

## <a name="see-also"></a>Consulte também
- [Intrínsecos do compilador](/cpp/intrinsics/compiler-intrinsics)
- [Segurança do depurador](../debugger/debugger-security.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)
- [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)