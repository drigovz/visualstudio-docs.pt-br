---
title: Autorização de proxy necessária | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848817691d7fae32f2240e3d6cac4451c4ce58c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297811"
---
# <a name="proxy-authorization-required"></a>Autorização de proxy necessária
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O erro de **autorização de proxy necessário** geralmente ocorre quando os usuários estão conectados aos recursos do Visual Studio online por meio de um servidor proxy e o servidor proxy bloqueia as chamadas.

Para corrigir esse erro, tente uma ou mais das seguintes etapas:

- Reinicie o Visual Studio. Uma caixa de diálogo de autenticação de proxy deverá aparecer. Insira suas credenciais na caixa de diálogo.

- Se a etapa acima não resolver o problema, pode ser porque o servidor proxy não solicita credenciais para endereços https://go.microsoft.com, mas sim para endereços *.visualStudio.com. Para esses servidores, você precisa adicionar as seguintes URLs à lista de permissões para desbloquear todos os cenários de entrada no Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Você pode remover o https://go.microsoft.com endereço da lista de permissões para que a caixa de diálogo de autenticação de proxy apareça para o https://go.microsoft.com endereço e os pontos de extremidade do servidor quando o Visual Studio for reiniciado.

- Se você quiser usar suas credenciais padrão com o proxy, faça o seguinte:

   1. Localize devenv.exe.config (o arquivo de configuração devenv.exe) em: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (ou **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. No arquivo de configuração, localize o bloco `<system.net>` e adicione esse código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insira o endereço de proxy correto para sua rede no `proxyaddress="<http://<yourproxy:port#>` .

- Siga as instruções nesta [postagem de blog](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) para adicionar código que permite que você use o proxy.
