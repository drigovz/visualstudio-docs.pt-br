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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f3522b61c8d7d78a182036d3a1f66c0495f5081
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852440"
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
