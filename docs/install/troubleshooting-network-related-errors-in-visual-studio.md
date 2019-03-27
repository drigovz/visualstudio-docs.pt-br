---
title: Solução de erros relacionados à rede ou ao proxy
description: Encontre soluções para erros relacionados à rede ou ao proxy que você pode encontrar ao instalar ou usar o Visual Studio por trás de um firewall ou um servidor proxy.
ms.date: 02/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4cd62e73d3a10eded5d74eaffc5486e237ca02ca
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324955"
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Solução de erros relacionados à rede ao instalar ou usar o Visual Studio

Temos soluções para os erros mais comuns relacionadas à rede ou ao proxy que você pode encontrar ao instalar ou usar o Visual Studio atrás de um firewall ou um servidor proxy.

## <a name="error-proxy-authorization-required"></a>Erro: “Autorização de proxy necessária”

Esse erro geralmente ocorre quando os usuários estão conectados à Internet por meio de um servidor proxy e o servidor proxy bloqueia as chamadas que o Visual Studio faz para alguns recursos de rede.

### <a name="to-fix-this-proxy-error"></a>Para corrigir esse erro de proxy

- Reinicie o Visual Studio. Uma caixa de diálogo de autenticação de proxy deverá aparecer. Insira suas credenciais na caixa de diálogo quando solicitado.

- Se reiniciar o Visual Studio não resolver o problema, talvez o servidor proxy não solicite credencias para endereços http:&#47;&#47;go.microsoft.com, mas solicite para endereços &#42;.visualStudio.com. Para esses servidores, considere adicionar à lista de permissões as seguintes URLs para desbloquear todos os cenários de conexão no Visual Studio:

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- Caso contrário, você pode remover o endereço de http:&#47;&#47;go.microsoft.com da lista de permissões para que a caixa de diálogo de autenticação de proxy apareça tanto para o endereço http:&#47;&#47;go.microsoft.com quanto para os pontos de extremidade do servidor quando o Visual Studio for reiniciado.

  -OU-

- Se você quiser usar suas credenciais padrão com o proxy, poderá realizar as seguintes ações:

  1. Localize **devenv.exe.config** (o arquivo de configuração devenv.exe) em: **%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** ou em **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

  2. No arquivo de configuração, localize o bloco `<system.net>` e adicione esse código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress="http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Você deve inserir o endereço de proxy correto para sua rede na `proxyaddress="<http://<yourproxy:port#>`.

     > [!NOTE]
     > Para obter mais informações, confira as páginas [Elemento &lt;defaultProxy&gt; (configurações de rede)](/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings) e [Elemento &lt;proxy&gt; (configurações de rede)](/dotnet/framework/configure-apps/file-schema/network/proxy-element-network-settings).

  -OU-

- Você também pode seguir as instruções na postagem no blog [How to connect through an authenticated Web Proxy](https://blogs.msdn.microsoft.com/rido/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy/) (Como se conectar por meio de um Proxy Web autenticado), que mostra como adicionar código que permitirá que você use o proxy.

## <a name="error-the-underlying-connection-was-closed"></a>Erro: “A conexão subjacente foi fechada”

Se você estiver usando o Visual Studio em uma rede privada que tem um firewall, o Visual Studio poderá não ser capaz de se conectar a alguns recursos da rede. Esses recursos podem incluir o Azure DevOps Services para conexão e licenciamento, o NuGet e os serviços do Azure. Se o Visual Studio falhar ao se conectar a um desses recursos, você deverá ver a seguinte mensagem de erro:

  **A conexão subjacente foi fechada: Erro inesperado no envio**

O Visual Studio usa o TLS (protocolo TLS) 1.2 para se conectar aos recursos de rede. Os dispositivos de segurança de algumas redes privadas bloqueiam determinadas conexões de servidor quando o Visual Studio usa o protocolo TLS 1.2.

### <a name="to-fix-this-connection-error"></a>Para corrigir esse erro de conexão

Habilite as conexões para as seguintes URLs:

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (para conexões do Azure)

- &#42;.visualstudio.com

- cdn.vsassets.io (hospeda conteúdo da rede de distribuição de conteúdo ou CDN)

- &#42;.gallerycdn.vsassets.io (hospeda extensões do Azure DevOps Services)

- static2.sharepointonline.com (hospeda recursos que o Visual Studio usa no kit do Office UI Fabric, como fontes)

- &#42;.nuget.org (para conexões NuGet)

  > [!NOTE]
  > As URLs de servidor NuGet privadas podem não estar incluídas nesta lista. Você pode verificar os servidores NuGet que estamos usando em %APPData%\Nuget\NuGet.Config.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar e usar o Visual Studio atrás de um firewall ou servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Instalar o Visual Studio](install-visual-studio.md)
