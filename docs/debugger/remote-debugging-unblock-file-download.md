---
title: Desbloquear o download das ferramentas remotas
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62903012"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Como: desbloquear o download das ferramentas remotas no Windows Server

As configurações de segurança padrão no Internet Explorer no Windows Server podem tornar o tempo demorado para baixar componentes como as ferramentas remotas.

* A configuração de segurança reforçada é habilitada no Internet Explorer, o que impede que você abra sites e acesse recursos da Web, a menos que o domínio que contém o recurso seja explicitamente permitido (ou seja, confiável). Embora você possa desabilitar essa configuração, isso não é recomendável porque pode representar um risco de segurança.

* No Windows Server 2016, uma configuração padrão em segurança de **Opções da Internet**  >  **Security**  >  **Internet**  >  downloads de**nível personalizado**da Internet  >  **Downloads** também desabilita os downloads de arquivo. Se você optar por baixar as ferramentas remotas diretamente no Windows Server, deverá habilitar o download do arquivo.

Para baixar as ferramentas no Windows Server, recomendamos um dos seguintes:

* Baixe as ferramentas remotas em um computador diferente, como aquele que está executando o Visual Studio, e copie o arquivo *. exe* para o Windows Server.

* Execute o depurador remoto [de um compartilhamento de arquivos](../debugger/remote-debugging.md#fileshare_msvsmon) no computador do Visual Studio.

* Baixe as ferramentas remotas diretamente no Windows Server e aceite os prompts para adicionar sites confiáveis. Os sites modernos geralmente incluem muitos recursos de terceiros, portanto, isso pode resultar em vários prompts. Além disso, todos os links redirecionados podem precisar ser adicionados manualmente. Você pode optar por adicionar alguns dos sites confiáveis antes de iniciar o download. Acesse **Opções da Internet > segurança > sites confiáveis > sites** e adicione os sites a seguir.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * sobre: em branco

  Para versões mais antigas do depurador no my.visualstudio.com, adicione esses sites adicionais para garantir que o logon seja bem-sucedido:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * Secure.aadcdn.microsoftonline p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Se você optar por adicionar esses domínios durante o download das ferramentas remotas, escolha **Adicionar** quando solicitado.

    ![Caixa de diálogo conteúdo bloqueado](../debugger/media/remotedbg-blocked-content.png)

    Ao baixar o software, você obtém algumas solicitações adicionais para conceder permissão para carregar vários recursos e scripts de site. No my.visualstudio.com, recomendamos que você adicione os domínios adicionais para garantir que o logon seja bem-sucedido.