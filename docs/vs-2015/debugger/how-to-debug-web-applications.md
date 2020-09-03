---
title: 'Como: depurar aplicativos Web | Microsoft Docs'
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205399"
---
# <a name="how-to-debug-web-applications"></a>Como depurar aplicativos Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é a principal tecnologia para o desenvolvimento de aplicativos Web no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . O depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornece ferramentas avançadas para depurar aplicativos Web do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] localmente ou em um servidor remoto. Este tópico descreve como depurar um [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projeto durante o desenvolvimento. Para obter informações sobre como depurar um [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicativo Web já implantado em um servidor de produção, consulte [Depurando aplicativos Web implantados](../debugger/debugging-deployed-web-applications.md).  
  
 Para depurar um aplicativo do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]:  
  
- Você deve ter as permissões necessárias. Para obter mais informações, veja [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] a depuração deve ser habilitada nas **Propriedades do projeto**.  
  
- O arquivo de configuração do aplicativo (Web.config) deve ser definido para o modo de depuração. O modo de depuração faz com que o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] gere símbolos para arquivos gerados dinamicamente e permite que o depurador se anexe ao aplicativo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] define isso automaticamente quando você começa a depurar, se você criou o projeto no modelo de projetos Web.  
  
- Para obter mais informações, consulte [como habilitar a depuração para aplicativos ASP.net](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Para depurar um aplicativo Web durante o desenvolvimento  
  
1. No menu **depurar** , clique em **Iniciar** para iniciar a depuração do aplicativo Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cria o projeto de aplicativo Web, implanta o aplicativo, se necessário, inicia a ASP.NET Development Server se você estiver Depurando localmente e anexa ao [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] processo de trabalho.  
  
2. Use o depurador para definir e desmarcar pontos de interrupção, depurar e executar outras operações de depuração, como faria para qualquer aplicativo.  
  
     Para obter mais informações, consulte [noções básicas do depurador](../debugger/debugger-basics.md).  
  
3. No menu **depurar** , clique em **parar depuração** para encerrar a sessão de depuração ou, no menu **arquivo** do Internet Explorer, clique em **fechar**.  
  
## <a name="see-also"></a>Consulte Também  
 [Depuração de scripts e aplicativos Web](../debugger/debugging-web-applications-and-script.md)   
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Instruções: habilitar a depuração para aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
