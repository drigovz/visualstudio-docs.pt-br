---
title: Autorização de proxy necessária | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b55dba438280fc4579fe15bd2a423d323c38abf6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54767271"
---
# <a name="proxy-authorization-required"></a>Autorização de proxy necessária
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Esse erro geralmente ocorre quando usuários estão conectados ao Visual Studio Online por meio de um servidor proxy e este bloqueia as chamadas. O Visual Studio Online é usado para manter o usuário conectado ao IDE.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Reinicie o Visual Studio. Uma caixa de diálogo de autenticação de proxy deverá aparecer. Insira suas credenciais na caixa de diálogo.  
  
-   Se a etapa acima não resolver o problema, pode ser porque o servidor proxy não solicita credenciais para endereços http://go.microsoft.com, mas sim para endereços *.visualStudio.com. Para esses servidores, você precisa colocar os seguintes itens na lista de permissões para desbloquear todos os cenários de credenciais no Visual Studio:  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   Caso contrário, você pode remover o http://go.microsoft.com de endereços da lista de permissões para que a caixa de diálogo de autenticação de proxy apareça para ambos o http://go.microsoft.com endereço e os pontos de extremidade do servidor quando o Visual Studio for reiniciado.  
  
-   OU  
  
-   Se você quiser usar suas credenciais padrão com o proxy, poderá fazer o seguinte:  
  
    1.  Localize devenv.exe.config (o arquivo de configuração devenv.exe) em: **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (ou **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2.  No arquivo de configuração, localize o bloco `<system.net>` e adicione esse código:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         Você deve inserir o endereço de proxy correto para sua rede na `proxyaddress="<http://<yourproxy:port#>`.  
  
-   OU  
  
-   Você também pode seguir as instruções [nesta postagem](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) para adicionar o código que permitirá o uso do proxy.
