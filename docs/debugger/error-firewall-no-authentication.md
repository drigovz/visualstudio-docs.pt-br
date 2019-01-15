---
title: 'Erro: Firewall sem autenticação | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
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
ms.openlocfilehash: a37fc9c1df938c1cb4817b74d2ebb1d239377823
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827228"
---
# <a name="error-firewall-no-authentication"></a>Erro: Firewall sem autenticação
O firewall de conexão da internet no computador remoto não está configurado para permitir a depuração remota. Para a depuração remota com `No Authentication`, o msvsmon.exe deve ser adicionado à lista de exceções. Abrir algumas portas de IPSEC pode ser necessário também.  
  
> [!NOTE]
>  O depurador remoto pode configurar automaticamente o Firewall do Windows. Ao usar um firewall diferente do Firewall do Windows como, por exemplo, o firewall do software de terceiros ou um firewall de hardware, o firewall deve ser configurado manualmente para permitir a depuração remota. Para fazer isso, permita o tráfego em portas TCP/IP no qual o msvsmon.exe está escutando. Por padrão, essas são as portas 4018 e 4019, onde 4018 é usado em todos os sistemas operacionais, e 4019 é usado apenas no Windows x64 para permitir depurar os processos x86.  
  
 Para obter mais informações, consulte [depuração remota](../debugger/remote-debugging.md).