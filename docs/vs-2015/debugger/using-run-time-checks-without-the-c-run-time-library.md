---
title: Usando verificações de tempo de execução sem a biblioteca de tempo de execução do C | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eefddd21817360736b9f20f74ca3dc8a83683fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684028"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>Usando verificações de tempo de execução sem a biblioteca em tempo de execução do C
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você vincular seu programa sem a biblioteca de tempo de execução C, usando **/NODEFAULTLIB**e quiser usar verificações de tempo de execução, será necessário vincular com RunTmChk. lib.  
  
 `_RTC_Initialize` Inicializa o programa para verificações de tempo de execução. Se você não se vincular à biblioteca em tempo de execução C, deverá verificar se o programa é compilado com verificações de erro em tempo de execução antes de chamar o `_RTC_Initialize`, do seguinte modo:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Se você não se vincular à biblioteca em tempo de execução C, também deverá definir uma função chamada `_CRT_RTC_INITW`. `_CRT_RTC_INITW` instala a função definida pelo usuário como a função de relatório de erros padrão, da seguinte maneira:  
  
```  
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
  
 Depois de instalar a função padrão de relatório de erros, você poderá instalar funções adicionais de relatório de erros com `_RTC_SetErrorFuncW`. Para obter mais informações, confira [_RTC_SetErrorFuncW](https://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Consulte Também  
 [Como: usar verificações nativas em tempo de execução](../debugger/how-to-use-native-run-time-checks.md)
