---
title: Não é possível iniciar a comunicação DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: 2ddae1685935cbb5267d3cc4f994c16e99a542da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870916"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erro: não é possível iniciar a comunicação DCOM
Um erro DCOM ocorreu quando o computador local tentou se comunicar com o computador remoto. Isso é causado por um firewall no servidor remoto ou por autenticação do Windows quebrada no computador remoto.

### <a name="to-correct-this-error"></a>Para corrigir este erro

- Se o computador remoto tiver o Firewall do Windows habilitado, consulte [depuração remota](../debugger/remote-debugging.md) para obter instruções sobre como configurar o firewall para depuração local.

- Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.

## <a name="see-also"></a>Consulte também
- [Depuração remota](../debugger/remote-debugging.md)