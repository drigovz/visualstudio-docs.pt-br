---
title: Localizar o processo ASP.NET em execução | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187661"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Localizar o nome do processo do ASP.NET

Para depurar um aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] em execução, o depurador do Visual Studio deve ser anexado ao processo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pelo nome.

**Para descobrir qual processo está executando um aplicativo ASP.NET:**

1. Com o aplicativo em execução, no Visual Studio, selecione **depurar** > **anexar ao processo**.

1. Na caixa de diálogo **anexar ao processo** , digite as primeiras letras dos nomes dos processos na lista a seguir ou insira-os na caixa de pesquisa. Aquele que está em execução é aquele que executa o aplicativo ASP.NET. Anexe a esse processo para depurar o aplicativo.

    - *w3wp. exe* é o IIS 6,0 e posterior.
    - *Aspnet_wp. exe* é uma versão anterior do IIS.
    - *iisexpress. exe* é iisexpress.
    - *dotnet. exe* ASP.NET Core.
    - o *Inetinfo. exe* é um aplicativo ASP mais antigo em execução no processo.

>[!NOTE]
>O Visual Studio 2012 e o código de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] anterior podem estar no sistema de arquivos e ser executados no servidor de teste *WebDev. WebServer. exe* ou *WebDev. WebServer40. exe*. Nesse caso, para a depuração local, anexe a *WebDev. WebServer. exe* ou *WebDev. WebServer40. exe* em vez do processo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**Confira também:**

- [Anexar a um processo em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Pré-requisitos para depuração remota de aplicativos Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)