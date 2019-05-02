---
title: 'Erro: Computador remoto não aparece em uma caixa de diálogo conexões remotas | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd194bc26574e8004894a72ce29d753cabf66a21
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850807"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Erro: O computador remoto não aparece em uma caixa de diálogo Conexões Remotas
Se o computador remoto não aparecer na caixa de diálogo conexões remotas, verifique as seguintes causas comuns.

 Se você estiver usando o modo de compatibilidade gerenciado, verifique a documentação do Visual Studio 2010: [Solucionando problemas de depuração remota - Visual Studio 2010](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/2ys11ead(v=vs.100)).

### <a name="common-causes-for-this-error"></a>Causas comuns desse erro

- O computador remoto está em execução em um computador que está em uma sub-rede diferente. Para corrigir isso, digite manualmente o nome do computador ou endereço IP na caixa de diálogo de qualificador

- O depurador remoto não está em execução no computador remoto. Para corrigir esse problema, inicie o depurador remoto.

- O firewall está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir esse problema, configure o firewall para permitir que o Visual Studio e o depurador remoto (msvsmon) para se comunicar.

- Software antivírus está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir esse problema, configure o software antivírus para permitir que o Visual Studio e o depurador remoto (msvsmon) para se comunicar.

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)