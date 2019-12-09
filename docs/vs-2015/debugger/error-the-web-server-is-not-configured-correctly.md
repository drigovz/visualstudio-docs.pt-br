---
title: 'Erro: o servidor Web não está configurado corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f5df9fb04849fce94d1a82748f2fc88f9577667
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297436"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Erro: o servidor Web não foi configurado corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Possíveis causas do erro incluem:  
  
- Tentando depurar um aplicativo Web do .NET que foi copiado para um computador diferente, renomeado manualmente ou movido.  
  
- Não ter conexões suficientes do IIS. Para obter mais informações sobre como implantar um site para o IIS, consulte [criar um site da Web](https://docs.microsoft.com/iis/get-started/getting-started-with-iis/create-a-web-site).  
  
- Se você estiver tentando depurar um aplicativo ASP.NET, consulte [publicando no IIS](https://docs.asp.net/en/latest/publishing/iis.html) para obter instruções sobre como implantar em um computador remoto que executa o IIS 8 ou superior, ou [a depuração remota ASP.net em um computador remoto do IIS 7,5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) para obter instruções sobre como implantar em um computador remoto que executa o IIS 7,5.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
