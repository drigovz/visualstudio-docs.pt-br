---
title: 'Depuração ASP.NET: requisitos do sistema | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa8951be6da4d77ffb51b6bc8f09a796b373a944
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826255"
---
# <a name="aspnet-debugging-system-requirements"></a>Depuração do ASP.NET: requisitos do sistema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico descreve os requisitos de software e de segurança para cenários de depuração do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Depuração local, na qual o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e o aplicativo Web são executados no mesmo computador. Há duas versões do controle desse cenário:  
  
  - O código do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] reside no sistema de arquivos.  

  - O código do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] reside em um site do IIS.  
  
- Depuração remota, na qual o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é executado em um computador cliente e depura um aplicativo Web que esteja em execução em um computador de servidor remoto.  
  
## <a name="security-requirements"></a>Requisitos de segurança  
 Para a depuração remota, os computadores locais e remotos devem estar em uma configuração de domínio ou em uma configuração de grupo de trabalho.  
  
 Para depurar o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], você deverá ter permissão para depurar esse processo. Por padrão, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] os aplicativos são executados como o usuário **ASPNET** . Se o processo de trabalho estiver sendo executado como **ASPNET** ou como **SERVIÇO DE REDE**, você deverá ter privilégios de administrador para depurá-lo.  
  
 O nome do processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia de acordo com o cenário de depuração e a versão do IIS. Para obter mais informações, consulte [como: localizar o nome do processo ASP.net](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Você pode alterar a conta de usuário sob a qual o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo de trabalho é executado editando o machine.config arquivo no servidor que está executando o IIS. A melhor maneira de fazer isso é usar o **Gerenciador do serviços de informações da Internet (IIS)**. Para obter mais informações, consulte [como: executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Se você alterar o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para ser executado em sua própria conta de usuário, não precisará ser um administrador no servidor que está executando o IIS.  
  
> [!CAUTION]
> Antes de alterar o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para ser executado em uma conta diferente, considere as possíveis consequências se o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] for invadido ao executar sob essa conta. As contas de usuário ASPNET and NETWORK SERVICE são executadas com as permissões mínimas, reduzindo o dano possível se o processo for invadido. Se você precisar alterar o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] para ser executado sob uma conta que tenha permissões maiores, o dano potencialmente será maior.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Como executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
