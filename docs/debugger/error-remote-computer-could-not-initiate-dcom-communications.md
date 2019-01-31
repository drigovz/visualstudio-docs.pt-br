---
title: 'Erro: Computador remoto não foi possível iniciar a comunicação DCOM | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
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
ms.openlocfilehash: a2612542a50d87b2fc8de50bf50955160c0b6f55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990817"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erro: O computador remoto não conseguiu iniciar as comunicações DCOM
Um erro DCOM ocorreu quando o computador remoto tentou se comunicar com o computador local. O computador local é o computador que está  
  
 executando o Visual Studio. Esse erro pode ocorrer por várias razões:  
  
-   O computador local tem um firewall habilitado.  
  
-   A autenticação do Windows do computador remoto para o computador local não está funcionando.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se o computador local tem o Firewall do Windows habilitado, consulte [depuração remota](../debugger/remote-debugging.md) para obter instruções sobre como configurar o firewall para depuração local.  
  
2.  Teste a autenticação do Windows tentando abrir um compartilhamento de arquivos no computador local do servidor remoto.  
  
3.  Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)