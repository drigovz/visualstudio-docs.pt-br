---
title: 'Depuração do ASP.NET: Requisitos do sistema | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, system requirements
- debugging ASP.NET Web applications, security requirements
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 334f2887b85cf0c58ace27cfca65984b29067246
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824032"
---
# <a name="aspnet-debugging-system-requirements"></a>Depuração do ASP.NET: Requisitos de sistema
Este tópico descreve os requisitos de software e de segurança para cenários de depuração do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
- Depuração local, na qual o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o aplicativo Web são executados no mesmo computador. Há duas versões do controle desse cenário:  
  
  - O código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside no sistema de arquivos.  
  
  - O código do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] reside em um site do IIS.  
  
- Depuração remota, na qual o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é executado em um computador cliente e depura um aplicativo Web que esteja em execução em um computador de servidor remoto.  
  
## <a name="security-requirements"></a>Requisitos de segurança  
 Para a depuração remota, os computadores locais e remotos devem estar em uma configuração de domínio ou em uma configuração de grupo de trabalho.  
  
 Para depurar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o processo de trabalho (hospedado por um Pool de aplicativos), você deve ter permissão para depurar esse processo. Por padrão, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos antes do IIS 6.0 são executados como a **ASPNET** usuário. No IIS 6.0 e IIS 7.0, o **serviço de rede** conta é o padrão. Se o processo de trabalho estiver sendo executado como **ASPNET** ou como **SERVIÇO DE REDE**, você deverá ter privilégios de administrador para depurá-lo.

 > [!IMPORTANT]
 > Começando com o Windows Server 2008 R2, recomendamos o uso do [ApplicationPoolIdentity](/iis/manage/configuring-security/application-pool-identities) como a identidade para cada pool de aplicativos.
  
 O nome do processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varia de acordo com o cenário de depuração e a versão do IIS. Para obter mais informações, confira [Como: Localizar o nome do processo do ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Você pode alterar o usuário da conta que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o processo de trabalho é executado, editando o arquivo Machine. config no servidor que está executando o IIS. A melhor maneira de fazer isso é usar o **serviços de informações da Internet (IIS) Manager**. Para obter mais informações, confira [Como: Executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Se você alterar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para ser executado em sua própria conta de usuário, não precisará ser um administrador no servidor que está executando o IIS.  
  
> [!CAUTION]
>  Antes de alterar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para ser executado em uma conta diferente, considere as possíveis consequências se o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] for invadido ao executar sob essa conta. As contas de usuário ASPNET and NETWORK SERVICE são executadas com as permissões mínimas, reduzindo o dano possível se o processo for invadido. Se você precisar alterar o processo de trabalho do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para ser executado sob uma conta que tenha permissões maiores, o dano potencialmente será maior.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Como: Executar o processo de trabalho em uma conta de usuário](../debugger/how-to-run-the-worker-process-under-a-user-account.md)