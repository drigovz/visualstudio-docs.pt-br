---
title: 'Erro: ASP.NET não instalado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838638"
---
# <a name="error-aspnet-not-installed"></a>Erro: ASP.NET não instalado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esse erro ocorre quando o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] não está instalado corretamente no computador que você está tentando depurar. Isso pode significar que o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nunca foi instalado ou que o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] foi instalado primeiro e o IIS foi instalado posteriormente.  
  
### <a name="to-reinstall-aspnet"></a>Para reinstalar o ASP.NET  
  
1. De uma janela de prompt de comando, execute o seguinte comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     em que *versão* representa o número de versão do .NET Framework instalado no computador, como v 1.0.370. Você pode determinar a versão do Framework examinando o `\WINDOWS\Microsoft.NET\Framework` diretório.  
  
    > [!NOTE]
    > Com o Windows Server 2003, você pode instalar o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] usando **Adicionar ou Remover Programas** no Painel de Controle.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
