---
title: 'Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41b1cef49425540980938b4d84a1825c171b271b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045688"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esse comportamento ocorre se uma das seguintes condições for verdadeira:  
  
- Sua conexão com o computador remoto foi interrompida.  
  
- Sua conta de usuário no computador remoto está desabilitada.  
  
- Sua senha no computador remoto expirou.  
  
### <a name="to-resolve-this-behavior"></a>Para resolver esse comportamento:  
  
- Verifique se o computador local e o computador remoto estão na mesma rede. Para fazer isso, use o Microsoft Windows Explorer (ou Pesquisador de Arquivos) para tentar acessar o computador remoto.  
  
     — e —  
  
- Verifique se a conta de usuário que você está usando para se conectar ao computador remoto está habilitada.  
  
     — e —  
  
- Verifique se a senha que você está usando para se conectar ao computador remoto está válida e não expirou.  
  
## <a name="see-also"></a>Consulte também  
 [Configurar as ferramentas remotas no dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)
