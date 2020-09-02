---
title: Funções de Hook de relatório | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687503"
---
# <a name="report-hook-functions"></a>Funções de gancho do relatório
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma função de gancho de relatório, instalada usando [_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509), é chamada sempre que [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) gera um relatório de depuração. Você pode usá-la, entre outras coisas, para filtrar relatórios com foco em tipos de alocações específicos. Uma função de gancho de relatório deve ter um protótipo como o seguinte:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 O ponteiro que você passa para **_CrtSetReportHook** é do tipo **_CRT_REPORT_HOOK**, conforme definido em CRTDBG. T  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando a biblioteca em tempo de execução chama sua função de gancho, o argumento de *nRptType* contém a categoria do relatório (**_CRT_WARN**, **_CRT_ERROR** ou **_CRT_ASSERT**), *szMsg* contém um ponteiro para uma cadeia de caracteres de mensagem de relatório completamente montada e *retVal* especifica se `_CrtDbgReport` deve continuar a execução normal depois de gerar o relatório ou iniciar o depurador. (Um valor de *retVal* igual a zero continua a execução, um valor igual a 1 inicia o depurador).  
  
 Se o gancho tratar completamente a mensagem em questão, de modo que nenhum relatório adicional seja necessário, ele retornará **TRUE**. Se retornar **false**, `_CrtDbgReport` relatará a mensagem normalmente.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar a gravação da função do gancho](../debugger/debug-hook-function-writing.md)   
 [Amostra de crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
