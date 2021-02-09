---
title: Tempo limite durante a depuração de serviços Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87a2d79fc24bdb433fbb5eb1480dbf5d15520a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871098"
---
# <a name="error-timeout-while-debugging-web-services"></a>Erro: tempo limite durante a depuração de serviços Web
Quando você estiver acessando um serviço Web XML do código de chamada, a chamada pode exceder o tempo limite e você não poderá continuar a depuração. Você pode ver uma mensagem de erro como essa.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Solução
 Para evitar esse problema, defina o tempo limite para a chamada ao serviço Web XML como infinito, conforme exibido neste exemplo:

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>Confira também
- [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
