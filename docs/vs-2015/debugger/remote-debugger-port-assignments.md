---
title: As atribuições de porta do depurador remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1e70ec3ba50e5be1ed532bb4a88cbdd500af09c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924532"
---
# <a name="remote-debugger-port-assignments"></a>Atribuições de porta do depurador remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador remoto do Visual Studio pode ser executado como um aplicativo ou como um serviço em segundo plano. Quando ele é executado como um aplicativo, ele usa uma porta atribuída por padrão, da seguinte maneira:  
  
- Visual Studio 2015: 4020  
  
- Visual Studio 2013: 4018  
  
- Visual Studio 2012: 4016  
  
  Em outras palavras, o número da porta atribuída ao depurador remoto é incrementado por 2 para cada versão. Você pode definir um número de porta diferente da que você deseja. Explicaremos como definir os números de porta em uma seção posterior.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>A porta do depurador remoto em sistemas operacionais de 32 bits  
 4020 TCP (no Visual Studio 2015) é a porta principal e é necessário para todos os cenários. Você pode configurar isso na linha de comando ou a janela do depurador remoto.  
  
 Na janela do depurador remoto, clique em **Ferramentas / opções**e defina o número da porta TCP/IP.  
  
 Na linha de comando, iniciar o depurador remoto com o **/porta** alternar: **msvsmon /port \<número da porta >**.  
  
 Você pode encontrar o depurador remoto de linha de comando na Ajuda de depuração remota (pressione **F1** ou clique em **ajuda / uso** na janela do depurador remoto).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>A porta do depurador remoto em sistemas operacionais de 64 bits  
 Quando a versão de 64 bits do depurador remoto é iniciada, ele usa a porta de 4020 por padrão.  Se você depurar um processo de 32 bits, a versão de 64 bits do depurador remoto inicia uma versão de 32 bits do depurador remoto na porta 4021. Se você executar o depurador remoto de 32 bits, ele usa 4020 e 4021 não é usado.  
  
 Essa porta é configurável na linha de comando: **O msvsmon /wow64port \<número da porta >**.  
  
## <a name="the-discovery-port"></a>A porta de descoberta  
 UDP 3702 é usada para localizar instâncias em execução do depurador remoto na rede (por exemplo, o **encontrar** caixa de diálogo na **anexar ao processo** caixa de diálogo). Ele é usado apenas para a descoberta de uma máquina executando o depurador remoto, portanto, é opcional se você tiver alguma outra maneira de saber o nome do computador ou endereço IP do computador de destino. Esta é uma porta padrão para a descoberta, portanto, o número da porta não pode ser configurado.  
  
 Se você não quiser habilitar a descoberta, você pode iniciar o msvsmon da linha de comando com a descoberta desabilitada:  **O msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Portas do depurador remoto no Azure  
 As seguintes portas são usadas pelo depurador remoto no Azure. As portas no serviço de nuvem são mapeadas para as portas na VM individual. Todas as portas são TCP.  
  
||||  
|-|-|-|  
|**conexão**|**Porta no serviço de nuvem**|**Porta na VM**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)
