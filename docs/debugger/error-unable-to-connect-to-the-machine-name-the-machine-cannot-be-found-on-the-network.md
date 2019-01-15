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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4c9bc3c72a2ff97fc67f31f44041feed2185551
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847367"
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