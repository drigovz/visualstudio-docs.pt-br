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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092000"
---
# <a name="error-rpc-requires-authentication"></a>Erro: O RPC requer autenticação
O depurador do Visual Studio não pode se conectar ao computador remoto. Uma política RPC está habilitada no computador local, impedindo a depuração remota.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Execute `\` *windir*`\system32\regedt32.exe`

2. Localize e exclua `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Reinicie o computador para que a alteração do Registro entre em vigor.

4. Se o problema persistir, entre em contato com seu administrador de domínio sobre o **configuração do computador > modelos administrativos > sistema > chamada de procedimento remoto > restrições para os clientes RPC não autenticados** política de grupo configuração.