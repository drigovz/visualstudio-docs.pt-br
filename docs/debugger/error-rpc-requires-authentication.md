---
title: RPC requer autenticação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09901453fc602deaa509ceb15e4c571764d407a4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871359"
---
# <a name="error-rpc-requires-authentication"></a>Erro: RPC requer autenticação
O depurador do Visual Studio não pode se conectar ao computador remoto. Uma política RPC está habilitada no computador local, impedindo a depuração remota.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Executar `\` *windir*`\system32\regedt32.exe`

2. Localizar e excluir `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Reinicie o computador para que a alteração do Registro entre em vigor.

4. Se o problema persistir, entre em contato com o administrador de domínio sobre a **configuração do computador > Modelos Administrativos > sistema > chamada de procedimento remoto > restrições para a configuração da política de grupo de clientes RPC não autenticados** .