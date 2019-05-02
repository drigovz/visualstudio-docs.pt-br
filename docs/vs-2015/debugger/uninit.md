---
title: UnInit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929274"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Finaliza o arquivo de log de gráficos, fecha e libera os recursos que foram usados enquanto o aplicativo ativamente estava gravando informações de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Comentários  
 `UnInit` é chamado automaticamente quando uma instância da `VsgDbg` classe seja destruída. Se o `VsgDbg` instância não estava gravando ativamente informações de gráficos, isso não tem nenhum efeito.  
  
 Após `UnInit` foi chamado em uma instância da `VsgDbg` classe, uma gráfico novo arquivo de log pode ser criado chamando `Init` e finalização, chamando `UnInit`. Você pode repetir isso quantas vezes você deseja usar o mesmo `VsgDbg` instância para criar gráficos independentes de vários arquivos de log.  
  
## <a name="see-also"></a>Consulte também  
 [Init](../debugger/init.md)
