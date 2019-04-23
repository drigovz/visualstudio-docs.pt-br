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
ms.openlocfilehash: b8eebd082df031161604bd04afe61d1aca652f6a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043278"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erro: Não é possível conectar à máquina &lt;nome&gt;. Não foi possível encontrar o computador na rede.
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
- [Depuração remota](../debugger/remote-debugging.md)
- [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)