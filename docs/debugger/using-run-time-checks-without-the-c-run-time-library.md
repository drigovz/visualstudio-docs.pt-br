---
title: Usando verificações de Run-Time sem a biblioteca C Run-Time | Microsoft Docs
description: Você pode vincular seu programa sem a biblioteca de tempo de execução do C usando/NODEFAULTLIB. Se você fizer isso e quiser usar verificações de tempo de execução, deverá vincular com RunTmChk. lib.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfa83533b1ae929bf443dd6c3eb7f7dc3e7db165
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150854"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Usando verificações de tempo de execução sem a biblioteca em tempo de execução do C
Se você vincular seu programa sem a biblioteca de tempo de execução C, usando **/NODEFAULTLIB** e quiser usar verificações de tempo de execução, será necessário vincular com RunTmChk. lib.

`_RTC_Initialize` Inicializa o programa para verificações de tempo de execução. Se você não se vincular à biblioteca em tempo de execução C, deverá verificar se o programa é compilado com verificações de erro em tempo de execução antes de chamar o `_RTC_Initialize`, do seguinte modo:

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

Se você não se vincular à biblioteca em tempo de execução C, também deverá definir uma função chamada `_CRT_RTC_INITW`. `_CRT_RTC_INITW` instala a função definida pelo usuário como a função de relatório de erros padrão, da seguinte maneira:

```cpp
// C version:
_RTC_error_fnW __cdecl _CRT_RTC_INITW(
        void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler.
    return &MyErrorFunc;
}

// C++ version:
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(
       void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler:
    return &MyErrorFunc;
}
```

Depois de instalar a função padrão de relatório de erros, você poderá instalar funções adicionais de relatório de erros com `_RTC_SetErrorFuncW`. Para obter mais informações, confira [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Confira também
[Como: usar verificações de Run-Time nativas](../debugger/how-to-use-native-run-time-checks.md)
