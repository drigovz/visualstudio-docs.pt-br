---
title: Usar o tempo de execução verifica sem a biblioteca de tempo de execução C | Microsoft Docs
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
ms.openlocfilehash: b440c2e95432dfa543d7e9aacae1256b27929de1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55020185"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Usando verificações de tempo de execução sem a biblioteca em tempo de execução do C
Se você vincular o programa sem a biblioteca de tempo de execução C, usando **/NODEFAULTLIB**e quiser usar verificações de tempo de execução, você deverá vincular com Runtmchk.  
  
 O `_RTC_Initialize` inicializa o programa para verificações de tempo de execução. Se você não se vincular à biblioteca em tempo de execução C, deverá verificar se o programa é compilado com verificações de erro em tempo de execução antes de chamar o `_RTC_Initialize`, do seguinte modo:  
  
```cpp
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Se você não se vincular à biblioteca em tempo de execução C, também deverá definir uma função chamada `_CRT_RTC_INITW`. O `_CRT_RTC_INITW` instala a função definida pelo usuário como a função padrão de relatório de erros, do seguinte modo:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Como: Usar verificações de tempo de execução nativas](../debugger/how-to-use-native-run-time-checks.md)
