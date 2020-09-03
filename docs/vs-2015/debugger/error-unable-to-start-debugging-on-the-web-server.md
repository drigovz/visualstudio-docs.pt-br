---
title: 'Erro: não é possível iniciar a depuração no servidor Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185480"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Erro: não foi possível iniciar a depuração no servidor Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao tentar depurar um aplicativo ASP.NET em execução em um servidor Web, você poderá receber esta mensagem de erro: não é possível iniciar a depuração no servidor Web.
  
Em muitos casos, esse erro ocorre porque o IIS não está configurado corretamente.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Verifique a configuração do IIS

Depois de seguir as etapas para resolver um problema detalhado aqui e antes de tentar depurar novamente, talvez você também precise redefinir o IIS. Você pode fazer isso abrindo um prompt de comando de administrador e digitando `iisreset` ou pode fazer isso no Gerenciador do IIS. 

* Pare e reinicie os pools de aplicativos e tente novamente.

    O pool de aplicativos pode ter sido interrompido ou outra alteração de configuração que você fez pode exigir que você pare e reinicie o pool de aplicativos.
    
    > [!NOTE]
    > Se o pool de aplicativos continuar a parar, talvez seja necessário desinstalar o módulo de reescrita de URL do painel de controle e reinstalá-lo usando o Web Platform Installer (WPI). Isso pode ser um problema após uma atualização significativa do sistema.

* Verifique a configuração do pool de aplicativos, corrija-o se necessário e tente novamente.

    Se as credenciais de senha forem alteradas, talvez seja necessário atualizá-las no pool de aplicativos. Além disso, se você instalou recentemente o ASP.NET, o pool de aplicativos poderá ser configurado para a versão incorreta do ASP.NET. Corrija o problema e reinicie o pool de aplicativos.
    
* Verifique se a pasta do aplicativo Web tem as permissões corretas.

    Certifique-se de conceder aos direitos de leitura e execução IIS_IUSRS ou IUSR (ou o usuário específico associado ao pool de aplicativos) para a pasta do aplicativo Web. Corrija o problema e reinicie o pool de aplicativos.

* Se você estiver usando um arquivo de HOSTs com endereços locais, tente usar o endereço de loopback em vez do endereço IP da máquina.

* Exibir a página localhost no navegador.

     Se o IIS não estiver instalado corretamente, você deverá obter erros ao digitar `http://localhost` um navegador.
     
     Para obter informações sobre como implantar no IIS, consulte [depuração remota ASP.net em um computador IIS remoto](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) ou, por ASP.NET Core, [publicando no IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Verifique se a versão correta do ASP.NET está instalada no IIS.  Consulte [implantar um aplicativo ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) ou, por ASP.NET Core, [publicando no IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Crie um aplicativo ASP.NET básico no servidor.

     Se você não puder fazer com que seu aplicativo funcione com o depurador, tente criar um aplicativo ASP.NET básico localmente no servidor e tente depurar o aplicativo básico. Se você puder depurar um aplicativo básico, isso poderá ajudá-lo a identificar o que há de diferente entre as duas configurações.
  
* Resolver erros de autenticação se você estiver usando apenas o endereço IP

     Por padrão, os endereços IP devem fazer parte da Internet e a autenticação NTLM não é feita pela Internet. Se o seu site estiver configurado no IIS para exigir autenticação, essa autenticação falhará. Para corrigir esse problema, você pode especificar o nome do computador remoto em vez do endereço IP.
     
## <a name="other-causes"></a>Outras causas

Se você estiver usando uma versão mais antiga do Visual Studio:

- Reinicie o Visual Studio com privilégios elevados e tente novamente.

    Um bug nas versões mais antigas (corrigidos posteriormente) exigiu privilégios elevados em alguns cenários de depuração ASP.NET.
    
- Se várias instâncias do Visual Studio estiverem em execução, abra novamente o projeto em uma instância do Visual Studio e tente novamente.

## <a name="see-also"></a>Consulte Também  
 [Depurando aplicativos Web: erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
