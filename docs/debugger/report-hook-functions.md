---
title: Funções de Hook de relatório | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0bb14b47fb17c4d59089aafa123115b85ab9342
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729867"
---
# <a name="report-hook-functions"></a>Funções de gancho do relatório
Uma função de gancho de relatório, instalada usando [_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook), é chamada sempre que [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) gera um relatório de depuração. Você pode usá-la, entre outras coisas, para filtrar relatórios com foco em tipos de alocações específicos. Uma função de gancho de relatório deve ter um protótipo como o seguinte:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 O ponteiro que você passa para **_CrtSetReportHook** é do tipo **_CRT_REPORT_HOOK**, conforme definido em CRTDBG. T

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Quando a biblioteca em tempo de execução chama sua função de gancho, o argumento de *nRptType* contém a categoria do relatório (**_CRT_WARN**, **_CRT_ERROR** ou **_CRT_ASSERT**), *szMsg* contém um ponteiro para uma cadeia de caracteres de mensagem de relatório completamente montada e *retVal* especifica se `_CrtDbgReport` deve continuar a execução normal depois de gerar o relatório ou iniciar o depurador. (Um valor de *retVal* igual a zero continua a execução, um valor igual a 1 inicia o depurador).

 Se o gancho tratar completamente a mensagem em questão, de modo que nenhum relatório adicional seja necessário, ele retornará **TRUE**. Se retornar **false**, `_CrtDbgReport` relatará a mensagem normalmente.

## <a name="see-also"></a>Confira também
- [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)
- [Amostra de crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
