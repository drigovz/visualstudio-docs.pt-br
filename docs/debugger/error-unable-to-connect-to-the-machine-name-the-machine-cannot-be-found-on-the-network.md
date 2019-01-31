---
title: 'Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9531151402b5070aaa3a680e09e0082b4e1237f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972034"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede.
Esse comportamento ocorre se uma das seguintes condições for verdadeira:  
  
-   Sua conexão com o computador remoto foi interrompida.  
  
-   Sua conta de usuário no computador remoto está desabilitada.  
  
-   Sua senha no computador remoto expirou.  
  
### <a name="to-resolve-this-behavior"></a>Para resolver esse comportamento:  
  
-   Verifique se o computador local e o computador remoto estão na mesma rede. Para fazer isso, use o Microsoft Windows Explorer (ou Pesquisador de Arquivos) para tentar acessar o computador remoto.  
  
     — e —  
  
-   Verifique se a conta de usuário que você está usando para se conectar ao computador remoto está habilitada.  
  
     — e —  
  
-   Verifique se a senha que você está usando para se conectar ao computador remoto está válida e não expirou.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)