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
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324613"
---
Essas etapas mostram apenas uma configuração básica do IIS. Para obter informações mais detalhadas ou instalar em um computador desktop com Windows, consulte [publicando no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) ou [iis 8,0 usando ASP.NET 3,5 e ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

Para sistemas operacionais Windows Server, use o assistente para **adicionar funções e recursos** por meio do link **gerenciar** link ou do **painel** no **Gerenciador do servidor**. Na etapa **Funções de Servidor**, marque a caixa de **Servidor Web (IIS)**.

![A função de Servidor Web IIS é selecionada na etapa Selecionar funções de servidor.](../media/remotedbg-server-roles-ws2012.png)

Na etapa **Serviços de função**, selecione os serviços de função do IIS desejados ou aceite os serviços de função padrão fornecidos. Se você quiser habilitar a implantação usando as configurações de publicação e Implantação da Web, verifique se a opções **scripts e ferramentas de gerenciamento do IIS** está selecionada.

Prossiga com as etapas de confirmação para instalar a função e os serviços do servidor Web. Uma reinicialização do servidor/IIS não é necessária após a instalação da função do Servidor Web (IIS).