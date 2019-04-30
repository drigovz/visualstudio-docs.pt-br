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
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906597"
---
Você deve ser capaz de depurar seu código com os símbolos que você gerar no computador do Visual Studio. O desempenho do depurador remoto é muito melhor quando você usa símbolos locais.  Se você precisar usar símbolos remotos, você precisa informar o monitor de depuração remota para procurar por símbolos no computador remoto.  

A partir do Visual Studio 2013 atualização 2, você pode usar a seguinte opção de linha de comando do msvsmon para usar símbolos remotos para código gerenciado: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Para obter mais informações, consulte a Ajuda de depuração remota (pressione **F1** na janela do depurador remoto, ou clique em **Ajuda > uso**). Você pode encontrar mais informações em [.NET Remote Symbol alterações de carregamento no Visual Studio 2012 e 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)
