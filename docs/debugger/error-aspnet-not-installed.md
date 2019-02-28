---
title: 'Erro: ASP.NET não instalado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 34ef8ef597c21230aa9ccdbd3146c07825753879
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680588"
---
# <a name="error-aspnet-not-installed"></a>Erro: ASP.NET não instalado
Esse erro ocorre quando o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não está instalado corretamente no computador que você está tentando depurar. Isso pode significar que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nunca foi instalado ou que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalado primeiro e o IIS foi instalado posteriormente.

### <a name="to-reinstall-aspnet"></a>Para reinstalar o ASP.NET

1. De uma janela de prompt de comando, execute o seguinte comando:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    em que *versão* representa o número de versão do .NET Framework instalado no seu computador, por exemplo, v1.0.370. Você pode determinar a versão do framework examinando o `\WINDOWS\Microsoft.NET\Framework` directory.

   > [!NOTE]
   >  Com o Windows Server 2003, você pode instalar o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando **Adicionar ou Remover Programas** no Painel de Controle.

## <a name="see-also"></a>Consulte também
- [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
