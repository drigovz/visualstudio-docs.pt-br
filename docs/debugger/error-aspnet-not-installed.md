---
title: ASP.NET não instalado
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 1c4138b1f3d102e235bb03ebcfd5a80808d8762c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852791"
---
# <a name="error-aspnet-not-installed"></a>Erro: ASP.NET não instalado
Esse erro ocorre quando o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não está instalado corretamente no computador que você está tentando depurar. Isso pode significar que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nunca foi instalado ou que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalado primeiro e o IIS foi instalado posteriormente.

### <a name="to-reinstall-aspnet"></a>Para reinstalar o ASP.NET

1. De uma janela de prompt de comando, execute o seguinte comando:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    em que *versão* representa o número de versão do .NET Framework instalado no computador, como v 1.0.370. Você pode determinar a versão do Framework examinando o `\WINDOWS\Microsoft.NET\Framework` diretório.

   > [!NOTE]
   > Com o Windows Server 2003, você pode instalar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando **Adicionar ou Remover Programas** no Painel de Controle.

## <a name="see-also"></a>Confira também
- [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
