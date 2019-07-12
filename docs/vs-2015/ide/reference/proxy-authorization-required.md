---
title: Autorização de proxy necessária | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f2de40c520bca0ea04f50ec782fec2dda531172e
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67822062"
---
# <a name="proxy-authorization-required"></a>Autorização de proxy necessária
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O **autorização de Proxy necessária** erro geralmente ocorre quando os usuários estão conectados aos recursos do Visual Studio online por meio de um servidor proxy e o servidor proxy bloqueia as chamadas.

Para corrigir esse erro, tente uma ou mais das seguintes etapas:

- Reinicie o Visual Studio. Uma caixa de diálogo de autenticação de proxy deverá aparecer. Insira suas credenciais na caixa de diálogo.

- Se a etapa acima não resolver o problema, pode ser porque o servidor proxy não solicita credenciais para endereços http://go.microsoft.com, mas sim para endereços *.visualStudio.com. Para esses servidores, você precisará adicionar as seguintes URLs à lista de permissões para desbloquear todos os cenários de entrar no Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Você pode remover o http://go.microsoft.com de endereços da lista de permissões para que a caixa de diálogo de autenticação de proxy apareça para ambos o http://go.microsoft.com endereço e os pontos de extremidade do servidor quando o Visual Studio for reiniciado.

- Se você quiser usar suas credenciais padrão com o proxy, faça o seguinte:

   1. Localize devenv.exe.config (o arquivo de configuração devenv.exe) em: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (ou **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. No arquivo de configuração, localize o bloco `<system.net>` e adicione esse código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insira o endereço de proxy correto para sua rede na `proxyaddress="<http://<yourproxy:port#>`.

- Siga as instruções em [esta postagem de blog](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) adicionar código que permite que você use o proxy.
