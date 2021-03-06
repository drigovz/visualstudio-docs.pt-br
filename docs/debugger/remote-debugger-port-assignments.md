---
title: Atribuições de porta do depurador remoto | Microsoft Docs
description: Entenda as atribuições de porta do depurador remoto do Visual Studio em sistemas operacionais de 32 bits, sistemas operacionais de 64 bits e Azure. Saiba mais sobre a porta de descoberta.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d7552ab67b70b3af8cfd1603462089e4fe2a209e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908209"
---
# <a name="remote-debugger-port-assignments"></a>Atribuições de porta do depurador remoto
O Depurador Remoto do Visual Studio pode ser executado como um aplicativo ou como um serviço em segundo plano. Quando ele é executado como um aplicativo, ele usa uma porta que é atribuída por padrão da seguinte maneira:
::: moniker range=">=vs-2019"
- Visual Studio 2019: 4024
::: moniker-end
- Visual Studio 2017: 4022

- Visual Studio 2015: 4020

- Visual Studio 2013: 4018

- Visual Studio 2012: 4016

Em outras palavras, o número da porta atribuída ao depurador remoto é incrementado por 2 para cada versão. Você pode definir um número de porta diferente, se desejar. Explicaremos como definir números de porta em uma seção posterior.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>A porta do depurador remoto em sistemas operacionais de 32 bits

::: moniker range=">=vs-2019"
 O TCP 4024 (no Visual Studio 2019) é a porta principal e é necessário para todos os cenários. Você pode configurá-lo na linha de comando ou na janela do depurador remoto.
::: moniker-end
::: moniker range="vs-2017"
 O TCP 4022 (no Visual Studio 2017) é a porta principal e é necessário para todos os cenários. Você pode configurá-lo na linha de comando ou na janela do depurador remoto.
::: moniker-end

 Na janela depurador remoto, clique em **ferramentas > opções** e defina o número da porta TCP/IP.

 Na linha de comando, inicie o depurador remoto com a opção **/Port** : **msvsmon/Port \<port number>**.

 Você pode encontrar todas as opções de linha de comando do depurador remoto na ajuda da depuração remota (pressione **F1** ou clique em **ajuda > uso** na janela do depurador remoto).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>A porta do depurador remoto em sistemas operacionais de 64 bits
::: moniker range=">=vs-2019"
 Quando a versão de 64 bits do depurador remoto é iniciada, ela usa a porta principal (4024) por padrão.  Se você depurar um processo de 32 bits, a versão de 64 bits do depurador remoto iniciará uma versão de 32 bits do depurador remoto na porta 4025 (o número da porta principal é incrementado em 1). Se você executar o depurador remoto de 32 bits, ele usará 4024 e 4025 não será usado.
::: moniker-end
::: moniker range="vs-2017"
 Quando a versão de 64 bits do depurador remoto é iniciada, ela usa a porta principal (4022) por padrão.  Se você depurar um processo de 32 bits, a versão de 64 bits do depurador remoto iniciará uma versão de 32 bits do depurador remoto na porta 4023 (o número da porta principal é incrementado em 1). Se você executar o depurador remoto de 32 bits, ele usará 4022 e 4023 não será usado.
:::moniker-end

 Essa porta é configurável na linha de comando: **msvsmon/wow64port \<port number>**.

## <a name="the-discovery-port"></a>A porta de descoberta
 O UDP 3702 é usado para localizar instâncias em execução do depurador remoto na rede (por exemplo, a caixa de diálogo **Localizar** na caixa de diálogo **anexar ao processo** ). Ele é usado apenas para descobrir um computador que executa o depurador remoto, portanto, é opcional se você tiver alguma outra forma de saber o nome do computador ou o endereço IP de um dos computadores de destino. Essa é uma porta padrão para descoberta, portanto, o número da porta não pode ser configurado.

 Se não quiser habilitar a descoberta, você poderá iniciar o msvsmon na linha de comando com a descoberta desabilitada:  **msvsmon/noDiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Portas do depurador remoto no Azure
 As portas a seguir são usadas pelo depurador remoto no Azure. As portas no serviço de nuvem são mapeadas para as portas na VM individual. Todas as portas são TCP.

|Conexão|Porta no serviço de nuvem|Porta na VM|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>Confira também
- [Depuração remota](../debugger/remote-debugging.md)
