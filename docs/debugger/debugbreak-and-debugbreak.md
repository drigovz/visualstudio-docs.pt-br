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
ms.openlocfilehash: 097405f98d1a80b8605b6773bdc675ff2c4ab773
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75404650"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak e __debugbreak
Você pode chamar a função Win32 [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) ou o [__debugbreak](/cpp/intrinsics/debugbreak) intrínseco em qualquer ponto em seu código. `DebugBreak` e `__debugbreak` têm o mesmo efeito de definir um ponto de interrupção nesse local.

 Como `DebugBreak` é uma chamada para uma função do sistema, os símbolos de depuração do sistema devem ser instalados para garantir que as informações corretas da pilha de chamadas sejam exibidas depois de interromper. Caso contrário, as informações da pilha de chamadas exibidas pelo depurador podem estar desativadas por um quadro. Se você usar `__debugbreak`, os símbolos não serão necessários.

## <a name="see-also"></a>Confira também
- [Intrínsecos do compilador](/cpp/intrinsics/compiler-intrinsics)
- [Segurança do depurador](../debugger/debugger-security.md)
- [Depurando código nativo](../debugger/debugging-native-code.md)
- [Especificar os arquivos de origem e símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
