---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912831"
---
Você deve ser capaz de depurar seu código com os símbolos que você gera no computador do Visual Studio. O desempenho do depurador remoto é muito melhor quando você usa símbolos locais.  Se for necessário usar símbolos remotos, você precisará instruir o monitor de depuração remota a procurar por símbolos no computador remoto.  

A partir do Visual Studio 2013 atualização 2, você pode usar a seguinte opção de linha de comando do msvsmon para usar símbolos remotos para código gerenciado: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Para obter mais informações, consulte a ajuda de depuração remota (pressione **F1** na janela do depurador remoto ou clique em **Ajuda > uso**). Você pode encontrar mais informações em [alterações de carregamento de símbolo remoto do .net no Visual Studio 2012 e 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
