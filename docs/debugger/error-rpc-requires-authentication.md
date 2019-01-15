---
title: 'Erro: O RPC requer autenticação | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66f319ba24a52a99994e693774aa9e7c0db7757e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874401"
---
# <a name="error-rpc-requires-authentication"></a>Erro: O RPC requer autenticação
O depurador do Visual Studio não pode se conectar ao computador remoto. Uma política RPC está habilitada no computador local, impedindo a depuração remota.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Execute `\` *windir*`\system32\regedt32.exe`  
  
2.  Localize e exclua `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie o computador para que a alteração do Registro entre em vigor.  
  
4.  Se o problema persistir, entre em contato com seu administrador de domínio sobre o **configuração do computador > modelos administrativos > sistema > chamada de procedimento remoto > restrições para os clientes RPC não autenticados** política de grupo configuração.