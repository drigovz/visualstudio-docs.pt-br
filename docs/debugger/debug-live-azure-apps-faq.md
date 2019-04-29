---
title: Perguntas frequentes sobre depuração de instantâneo | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62853319"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Perguntas frequentes sobre depuração de instantâneo no Visual Studio

Veja a seguir uma lista de perguntas que podem surgir durante a depuração de aplicativos dinâmicos do Azure usando o Depurador de Instantâneos.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Qual é o custo de desempenho de capturar um instantâneo?

Quando o Depurador de Instantâneos captura um instantâneo do seu aplicativo, ele bifurca o processo do aplicativo e suspende a cópia bifurcada. Ao depurar um instantâneo, você o está depurando em relação à cópia bifurcada do processo. Esse processo leva apenas 10 a 20 milissegundos, mas não copia o heap completo do aplicativo. Em vez disso, copia apenas a tabela de página e define as páginas para cópia na gravação. Se algum dos objetos do seu aplicativo no heap for alterado, as respectivas páginas serão copiadas. Isso porque cada instantâneo tem um pequeno custo na memória (na ordem de centenas de kilobytes para a maioria dos aplicativos).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>O que acontece se eu tiver um Serviço de Aplicativo do Azure expandido (várias instâncias do meu aplicativo)?

Quando você tiver várias instâncias do seu aplicativo, os snappoints serão aplicados a cada instância única. Somente o primeiro snappoint a atender às condições especificadas cria um instantâneo. Se você tiver vários snappoints, instantâneos posteriores serão provenientes da mesma instância que criou o primeiro instantâneo. Logpoints enviados para a janela de saída mostrarão apenas as mensagens de uma instância, enquanto logpoints enviados para os logs de aplicativo enviarão mensagens de todas as instâncias.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Como o Depurador de Instantâneos carrega símbolos?

O Depurador de Instantâneos requer que você tenha os símbolos correspondentes para seu aplicativo no local ou implantados no Serviço de Aplicativo do Azure. (No momento, não há suporte para PDBs inseridos). O Depurador de Instantâneos baixa automaticamente os símbolos de seu Serviço de Aplicativo do Azure. A partir do Visual Studio 2017 versão 15.2, a implantação no Serviço de Aplicativo do Azure também faz a implantação dos símbolos do seu aplicativo.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>O Depurador de Instantâneos funciona em builds de versão do meu aplicativo?

Sim, o Depurador de Instantâneos deve funcionar em builds de versão. Quando um snappoint for colocado em uma função, a função será recompilada para uma versão de depuração, tornando-o depurável. A interrupção do Depurador de Instantâneos retorna funções para a versão do build de versão.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Os logpoints pode causar efeitos colaterais no meu aplicativo de produção?

Não. As mensagens de log que você adiciona ao seu aplicativo são avaliadas virtualmente. Elas não podem causar efeitos colaterais em seu aplicativo. No entanto, algumas propriedades nativas podem não ser acessíveis com logpoints.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>O Depurador de Instantâneos funcionará se meu servidor estiver sob carga?

Sim, a depuração de instantâneos pode funcionar em servidores sob carga. O Depurador de Instantâneos faz a restrição e não captura instantâneos em situações em que há uma quantidade pequena de memória livre em seu servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Como faço para desinstalar o Depurador de Instantâneos?

Você pode desinstalar a extensão de site do Depurador de Instantâneos no seu Serviço de Aplicativo com as seguintes etapas:

1. Desative o Serviço de Aplicativo por meio do Cloud Explorer no Visual Studio ou no portal do Azure.
1. Navegue até o site do Kudu do Serviço de Aplicativo (ou seja, seu serviçodeaplicativo.**scm**.azurewebsites.net) e vá até **Extensões de Site**.
1. Clique no X na extensão de site do Depurador de Instantâneos para removê-lo.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Por que as portas ficam abertas durante uma sessão do Depurador de Instantâneos?

O Depurador de Instantâneos precisa abrir um conjunto de portas para depurar os instantâneos tirados no Azure. São as mesmas portas necessárias para depuração remota. [Encontre a lista de portas aqui](../debugger/remote-debugger-port-assignments.md).

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.md)
- [Depurar aplicativos ASP.NET dinâmicos usando o depurador de instantâneo](../debugger/debug-live-azure-applications.md)
- [Depurar ao vivo ASP.NET Azure Virtual Machines\Virtual máquinas conjuntos de dimensionamento usando o depurador de instantâneo](../debugger/debug-live-azure-virtual-machines.md)
- [Depurar ao vivo ASP.NET Azure Kubernetes usando o depurador de instantâneo](../debugger/debug-live-azure-kubernetes.md)
- [Solução de problemas e problemas conhecidos para depuração de instantâneo](../debugger/debug-live-azure-apps-troubleshooting.md)