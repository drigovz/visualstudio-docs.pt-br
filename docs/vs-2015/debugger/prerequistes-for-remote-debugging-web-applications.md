---
title: Pré-requisitos para aplicativos Web de depuração remota | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 448e6e7705e4df7330abce0e919adc705721102c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227277"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Pré-requisitos para aplicativos Web de depuração remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com o depurador do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você pode depurar um aplicativo Web de maneira transparente no computador local ou em um servidor remoto. Isso significa que o depurador funciona da mesma maneira e permite que você use os mesmos recursos em qualquer computador. Para que a depuração remota funcione corretamente, no entanto, há alguns pré-requisitos.  
  
-   Os componentes da depuração remota do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] devem estar instalados no servidor que você deseja depurar. Para obter mais informações, consulte [Configurando a depuração remota](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
-   Por padrão, o processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado como um processo de usuário do ASPNET. Como resultado, você deve ter privilégios de Administrador no computador no qual o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] é executado para depurá-lo. O nome do processo de trabalho do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] varia de acordo com o cenário de depuração e a versão do IIS. Para obter mais informações, consulte [como: localizar o nome do processo do ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisitos do sistema](../debugger/aspnet-debugging-system-requirements.md)



