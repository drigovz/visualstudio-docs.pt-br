---
title: Pré-requisitos para depuração remota de aplicativos Web | Microsoft Docs
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
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8cbf0ae920be00980d270aae16d5e7d1f7a5313
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574624"
---
# <a name="prerequisites-for-remote-debugging-web-applications"></a>Pré-requisitos para depuração remota de aplicativos Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com o depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você pode depurar um aplicativo Web de maneira transparente no computador local ou em um servidor remoto. Isso significa que o depurador funciona da mesma maneira e permite que você use os mesmos recursos em qualquer computador. Para que a depuração remota funcione corretamente, no entanto, há alguns pré-requisitos.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] componentes de depuração remota devem ser instalados no servidor que você deseja depurar. Para obter mais informações, consulte [Configurando a depuração remota](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Por padrão, o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado como um processo de usuário do ASPNET. Como resultado, você deve ter privilégios de Administrador no computador no qual o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado para depurá-lo. O nome do processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia de acordo com o cenário de depuração e a versão do IIS. Para obter mais informações, consulte [como: localizar o nome do processo ASP.net](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)
