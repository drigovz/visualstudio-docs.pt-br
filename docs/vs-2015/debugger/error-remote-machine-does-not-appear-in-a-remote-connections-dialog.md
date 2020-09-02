---
title: 'Erro: o computador remoto não aparece em uma caixa de diálogo conexões remotas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a97211c1fa86123a2a7a65f2ff86b0cecac957dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697321"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Erro: o computador remoto não aparece em uma caixa de diálogo Conexões Remotas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se o computador remoto não aparecer na caixa de diálogo conexões remotas, verifique as causas comuns a seguir.  
  
 Se você estiver usando o modo de compatibilidade gerenciado, consulte a documentação do Visual Studio 2010: [solução de problemas de depuração remota-Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Causas comuns desse erro  
  
- O computador remoto está em execução em um computador que está em uma sub-rede diferente. Para corrigir isso, digite manualmente o nome do computador ou o endereço IP na caixa de diálogo qualificador  
  
- O depurador remoto não está em execução no computador remoto. Para corrigir isso, inicie o depurador remoto.  
  
- O firewall está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir isso, configure o firewall para permitir que o Visual Studio e o depurador remoto (msvsmon) se comuniquem.  
  
- O software antivírus está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir isso, configure o software antivírus para permitir que o Visual Studio e o o depurador remoto (msvsmon) se comuniquem.  
  
## <a name="see-also"></a>Consulte Também  
 [Configurar as ferramentas remotas no dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
