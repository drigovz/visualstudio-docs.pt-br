---
title: UnInit | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8165b2e1993a6ea52127536a058f662e1a3d92cc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848725"
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
- [Init](init.md)