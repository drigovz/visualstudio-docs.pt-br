---
title: Depurar aplicativos de 64 bits | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56e5b76b000fd269d76d535e635ba86e72912bad
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915999"
---
# <a name="debug-64-bit-applications"></a>Depurar aplicativos de 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [aplicativos de depuração de 64 bits](/visualstudio/debugger/debug-64-bit-applications) .  
  
Você pode depurar um aplicativo de 64 bits que está sendo executado no computador local ou em um computador remoto.  
  
 Para depurar um aplicativo de 64 bits que está sendo executado em um computador remoto, consulte [depuração remota](../debugger/remote-debugging.md).  
  
 Para depurar aplicativos de 64 bits localmente, o Visual Studio usa um processo de trabalho de 64 bits (msvsmon. exe) para executar as operações de nível baixo que não podem ser feitas dentro do processo do Visual Studio de 32 bits.  
  
 Não há suporte para a depuração de modo misto em processos de 64 bits que usam .NET Framework versão 3,5 ou anterior.  
  
## <a name="debug-a-64-bit-application"></a>Depurar um aplicativo de 64 bits  
 Para tentar depurar um aplicativo de 64 bits:  
  
1. Crie uma solução do Visual Studio, por exemplo C# , um aplicativo de console.  
  
2. Defina a configuração como 64 bits usando o Configuration Manager. Para obter mais informações, consulte [como: configurar projetos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3. Neste ponto, a versão de 64 bits do depurador remoto (msvsmon. exe) é iniciada. Ele é executado contanto que a solução com a configuração de 64 bits esteja aberta.  
  
4. Inicie a depuração. Você deve ter a mesma experiência que com uma configuração de 32 bits. Se você receber erros, consulte a seção solução de problemas abaixo.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Solução de problemas de depuração de 64 bits  
 Você pode ver um erro: "uma operação de depuração de 64 bits está demorando mais do que o esperado". Nesse caso, o Visual Studio enviou uma solicitação para a versão de 64 bits do msvsmon. exe e levou muito tempo para que o resultado dessa solicitação volte.  
  
 Há duas causas principais para esse erro:  
  
- Você tem um software de segurança de rede instalado no seu computador que fez com que a pilha de rede não seja confiável e tenha descartado pacotes passando por localhost. Tente desabilitar todos os softwares de segurança de rede e ver se isso o resolve. Nesse caso, relate ao fornecedor do software de segurança de rede que o software está interferindo com o tráfego de localhost.  
  
- Você está ficando com um problema de interrupção ou desempenho com o Visual Studio. Se o problema ocorrer regularmente, você poderá coletar despejos do Visual Studio (devenv. exe) e do processo de trabalho (msvsmon. exe) e enviá-los à Microsoft. 
  
## <a name="see-also"></a>Veja também  
 [Aplicativos de 64 bits](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Configurando programas para 64 bits](https://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Suporte ao IDE do Visual Studio de 64 bits](../ide/visual-studio-ide-64-bit-support.md)   
 [Usando arquivos de despejo](../debugger/using-dump-files.md)   
 [Depuração remota](../debugger/remote-debugging.md)
