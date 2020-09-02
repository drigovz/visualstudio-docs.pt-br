---
title: 'Erro: RPC requer autenticação | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535730"
---
# <a name="error-rpc-requires-authentication"></a>Erro: RPC requer autenticação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador do Visual Studio não pode se conectar ao computador remoto. Uma política RPC está habilitada no computador local, impedindo a depuração remota.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Executar `\` *windir*`\system32\regedt32.exe`  
  
2. Localizar e excluir `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .  
  
3. Reinicie o computador para que a alteração do Registro entre em vigor.  
  
4. Se o problema persistir, entre em contato com o administrador de domínio sobre a **configuração do computador->modelos administrativos->o sistema >chamada de procedimento remoto->restrições para clientes RPC não autenticados configuração da política de** grupo.
