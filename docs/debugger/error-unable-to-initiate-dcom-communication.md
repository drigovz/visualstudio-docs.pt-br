---
title: 'Erro: Não é possível iniciar a comunicação DCOM | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 89dc5ba98d706153b919063563f1d4beecacdde5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932058"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erro: Não é possível iniciar a comunicação DCOM
Um erro DCOM ocorreu quando o computador local tentou se comunicar com o computador remoto. Isso é causado por um firewall no servidor remoto ou por autenticação do Windows quebrada no computador remoto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o computador remoto tiver o Firewall do Windows habilitado, consulte [depuração remota](../debugger/remote-debugging.md) para obter instruções sobre como configurar o firewall para depuração local.  
  
-   Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)