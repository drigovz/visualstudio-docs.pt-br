---
title: 'Erro: Não é possível intervir automaticamente no servidor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9d84f4c7f7f58ae980a266b436207c843926ae1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850138"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Erro: Não é possível intervir no servidor automaticamente
O erro é:

 Não é possível realizar a depuração completa do servidor automaticamente. O depurador não foi notificado antes do procedimento remoto ter sido executado

 Esse erro pode ocorrer quando você está tentando entrar em um serviço Web (confira [Entrar em um serviço Web XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Pode ocorrer sempre que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não estiver configurado corretamente.

 Possíveis causas:

- O arquivo web.config do aplicativo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não define a depuração como “true” em (confira [Modo de depuração em aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Uma versão do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalada depois que o Visual Studio foi instalado. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] deve ser instalado antes do Visual Studio. Para corrigir esse problema, use o **Painel de Controle, Programas e Recursos do Windows** para reparar a instalação do Visual Studio.

## <a name="see-also"></a>Consulte também
- [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Depuração remota](../debugger/remote-debugging.md)