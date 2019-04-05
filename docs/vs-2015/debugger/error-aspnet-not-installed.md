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
ms.openlocfilehash: 31268b94ab632e598badcba3def387ef1fc2ba1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58921765"
---
# <a name="error-aspnet-not-installed"></a>Erro: ASP.NET não instalado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esse erro ocorre quando o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] não está instalado corretamente no computador que você está tentando depurar. Isso pode significar que o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nunca foi instalado ou que o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] foi instalado primeiro e o IIS foi instalado posteriormente.  
  
### <a name="to-reinstall-aspnet"></a>Para reinstalar o ASP.NET  
  
1.  De uma janela de prompt de comando, execute o seguinte comando:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     em que *versão* representa o número de versão do .NET Framework instalado no seu computador, por exemplo, v1.0.370. Você pode determinar a versão do framework examinando o `\WINDOWS\Microsoft.NET\Framework` directory.  
  
    > [!NOTE]
    >  Com o Windows Server 2003, você pode instalar o [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] usando **Adicionar ou Remover Programas** no Painel de Controle.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
