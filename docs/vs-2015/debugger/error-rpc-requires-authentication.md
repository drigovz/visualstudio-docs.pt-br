---
title: 'Erro: RPC requer autenticação | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5643e815386541bb9045eb56cacbd68e7e9b998d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193824"
---
# <a name="error-rpc-requires-authentication"></a>Erro: RPC requer autenticação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O depurador do Visual Studio não pode se conectar ao computador remoto. Uma política RPC está habilitada no computador local, impedindo a depuração remota.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Execute `\` *windir*`\system32\regedt32.exe`  
  
2.  Localize e exclua `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie o computador para que a alteração do Registro entre em vigor.  
  
4.  Se o problema persistir, entre em contato com seu administrador de domínio sobre o **configuração do computador -> modelos administrativos - > sistema -> Remote chamada de procedimento -> restrições para os clientes RPC não autenticados** grupo configuração de política.



