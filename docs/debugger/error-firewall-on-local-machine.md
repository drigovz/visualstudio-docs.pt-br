---
title: 'Erro: Firewall no computador Local | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: 87a1813410a092ced335f37b9df4cf6547ca1cc3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715759"
---
# <a name="error-firewall-on-local-machine"></a>Erro: firewall na máquina local
O firewall de conexão da Internet no computador local, o computador no qual você está executando o Visual Studio, não está configurado para permitir a depuração remota. Para a depuração remota gerenciada ou nativa com o transporte padrão, a porta TCP 135 deve estar aberta para o tráfego de DCOM. O compartilhamento de arquivos e impressoras deve ser aberto e o devenv.exe deve ser adicionado à lista de exceções. Abrir algumas portas de IPSEC pode ser necessário também.

 Para obter mais informações, consulte [depuração remota](../debugger/remote-debugging.md).