---
title: Download do depurador remoto
description: Links de download para o depurador remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67032884"
---
No dispositivo remoto ou servidor que você deseja depurar na, em vez de computador do Visual Studio, baixe e instale a versão correta das ferramentas remotas nos links na tabela a seguir.

- Baixe as mais recentes ferramentas remotas para a sua versão do Visual Studio. A versão mais recente de ferramentas remoto é compatível com versões anteriores do Visual Studio, mas as versões anteriores de ferramentas remotas não são compatíveis com versões posteriores do Visual Studio. (Por exemplo, se você estiver usando o Visual Studio 2017, baixe a atualização mais recente das ferramentas remotas para Visual Studio 2017. Nesse cenário, não baixe as ferramentas remotas para Visual Studio de 2019.)
- Baixe as ferramentas remotas com a mesma arquitetura que a máquina que você estiver instalando-os em. Por exemplo, se você quiser depurar um aplicativo de 32 bits em um computador remoto executando um sistema operacional de 64 bits, instale as ferramentas remotas de 64 bits.

::: moniker range=">=vs-2019"

|Versão|Link|Observações|
|-|-|-|
|Visual Studio 2019|[Ferramentas remotas](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|É compatível com todas as versões do Visual Studio de 2019. Baixe a versão correspondente do seu sistema operacional do dispositivo (x x86, x64 ou ARM64). No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging-unblock-file-download.md) para obter ajuda a baixar as ferramentas remotas.|
|Visual Studio 2017|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|É compatível com todas as versões do Visual Studio 2017. Baixe a versão correspondente do seu sistema operacional do dispositivo (x x86, x64 ou ARM64). No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging-unblock-file-download.md) para obter ajuda a baixar as ferramentas remotas.|
|Visual Studio 2015|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Ferramentas remotas para Visual Studio 2015 estão disponíveis no My.VisualStudio.com. Se solicitado, Junte-se a versão gratuita [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programa, ou entre com sua ID de assinatura do Visual Studio. No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging-unblock-file-download.md) para obter ajuda a baixar as ferramentas remotas.|
|Visual Studio 2013|[Ferramentas remotas](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Baixar a página na documentação do Visual Studio 2013|
|Visual Studio 2012|[Ferramentas remotas](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Baixar a página na documentação do Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Versão|Link|Observações|
|-|-|-|
|Visual Studio 2017|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|É compatível com todas as versões do Visual Studio 2017. Baixe a versão correspondente do seu sistema operacional do dispositivo (x x86, x64 ou ARM64). No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging-unblock-file-download.md) para obter ajuda a baixar as ferramentas remotas. Para obter a versão mais recente das ferramentas remotas, abra o [Visual Studio de 2019 doc](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[Ferramentas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Ferramentas remotas para Visual Studio 2015 estão disponíveis no My.VisualStudio.com. Se solicitado, Junte-se a versão gratuita [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programa, ou entre com sua ID de assinatura do Visual Studio. No Windows Server, consulte [desbloquear o download do arquivo](../../debugger/remote-debugging-unblock-file-download.md) para obter ajuda a baixar as ferramentas remotas.|
|Visual Studio 2013|[Ferramentas remotas](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Baixar a página na documentação do Visual Studio 2013|
|Visual Studio 2012|[Ferramentas remotas](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Baixar a página na documentação do Visual Studio 2012|

::: moniker-end

Você pode executar o depurador remoto copiando *msvsmon.exe* para o computador remoto, em vez de instalar as ferramentas remotas. No entanto, o Assistente de configuração do depurador remoto (*rdbgwiz.exe*) está disponível apenas quando você instala as ferramentas remotas. Talvez você precise usar o Assistente para configuração, se você quiser executar o depurador remoto como um serviço. Para obter mais informações, consulte [(opcional) configurar o depurador remoto como um serviço](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Para depurar aplicativos do Windows 10 em dispositivos ARM, use ARM64, que está disponível com a versão mais recente das ferramentas remotas.
>- Para depurar aplicativos do Windows 10 em dispositivos Windows RT, use o ARM, que está disponível apenas no Visual Studio 2015 download das ferramentas remotas.
