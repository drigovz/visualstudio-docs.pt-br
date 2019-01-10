---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1cb7898042ef7f6974d2ac43ca8630232edddfc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53884922"
---
# <a name="uninit"></a>UnInit
Finaliza o arquivo de log de gráficos, fecha e libera os recursos que foram usados enquanto o aplicativo ativamente estava gravando informações de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Comentários  
 `UnInit` é chamado automaticamente quando uma instância da `VsgDbg` classe seja destruída. Se o `VsgDbg` instância não estava gravando ativamente informações de gráficos, isso não tem nenhum efeito.  
  
 Após `UnInit` foi chamado em uma instância da `VsgDbg` classe, uma gráfico novo arquivo de log pode ser criado chamando `Init` e finalização, chamando `UnInit`. Você pode repetir isso quantas vezes você deseja usar o mesmo `VsgDbg` instância para criar gráficos independentes de vários arquivos de log.  
  
## <a name="see-also"></a>Consulte também  
 [Init](init.md)