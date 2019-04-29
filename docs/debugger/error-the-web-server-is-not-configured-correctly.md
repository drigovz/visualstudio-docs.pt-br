---
title: 'Erro: O servidor web não está configurado corretamente | Microsoft Docs'
ms.date: 09/20/2017
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc0c61b766b6f93fd1321b15861000d7c628f124
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850406"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Erro: O servidor Web não foi configurado corretamente

Depois de obter as etapas descritas aqui para resolver o problema e antes de tentar novamente a depuração, você também precisará redefinir o IIS. Você pode fazer isso abrindo um prompt de comando do administrador e digitando `iisreset`.

Siga estas etapas para resolver esse problema:

1. Se o aplicativo web hospedado no servidor é configurado como um build de versão, publicar novamente como um build de depuração e verifique se o arquivo Web. config contém `debug=true` no elemento compilation. Redefina o IIS e tente novamente.

    Por exemplo, se você estiver usando um perfil de publicação para um build de versão, alterá-lo para depuração e republicar. Caso contrário, o atributo será definido como `false` quando você publica.

2. (IIS) Verifique se o caminho físico está correto. No IIS, você pode encontrar essa configuração no **configurações básicas > caminho físico** (ou **configurações avançadas** em versões anteriores do IIS).

    O caminho físico pode estar incorreto se o aplicativo web foi copiado para um computador diferente, manualmente renomeado ou movido. Redefina o IIS e tente novamente.

3. Se você estiver depurando localmente no Visual Studio, verifique se o servidor correto está selecionado nas propriedades. (Abra **Propriedades > Web > servidores** ou **Propriedades > Depurar** dependendo do seu tipo de projeto. Para um projeto de formulários da Web, abra **páginas de Propriedades > Opções de inicialização > servidor**).

    Se você estiver usando um servidor externo (personalizado), como o IIS, a URL deve estar correta. Caso contrário, selecione o IIS Express e tente novamente.

4. (IIS) Certifique-se de que a versão correta do ASP.NET está instalada no servidor.

    Versões incompatíveis do ASP.NET no IIS e no projeto do Visual Studio podem causar esse problema. Talvez você precise definir a versão do framework no Web. config. Para instalar o ASP.NET no IIS, use o [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consulte também [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ou, para o ASP.NET Core [Host no Windows com o IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Se o `maxConnection` limite no IIS for muito baixo e você tem muitas conexões, talvez você precise [aumentar o limite de conexão](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Consulte também
- [Depuração Remota de ASP.NET em um computador remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)