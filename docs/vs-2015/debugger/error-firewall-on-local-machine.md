---
title: 'Erro: Firewall no computador Local | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 23290ebb12c2cb3e6bb12554aa9fbb89c4fb82fa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925550"
---
# <a name="error-firewall-on-local-machine"></a>Erro: Firewall no computador local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O firewall de conexão da Internet no computador local, o computador no qual você está executando o Visual Studio, não está configurado para permitir a depuração remota. Para a depuração remota gerenciada ou nativa com o transporte padrão, a porta TCP 135 deve estar aberta para o tráfego de DCOM. O compartilhamento de arquivos e impressoras deve ser aberto e o devenv.exe deve ser adicionado à lista de exceções. Abrir algumas portas de IPSEC pode ser necessário também.  
  
 Para obter mais informações, consulte [definir configurar as ferramentas remotas no dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).
