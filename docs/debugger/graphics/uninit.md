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
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734815"
---
# <a name="uninit"></a>UnInit
Finaliza o arquivo de log de gráficos, fecha-o e libera os recursos que foram usados enquanto o aplicativo gravava informações gráficas ativamente.

## <a name="syntax"></a>Sintaxe

```C++
void UnInit();
```

## <a name="remarks"></a>Comentários
 `UnInit` é chamado automaticamente quando uma instância da classe `VsgDbg` é destruída. Se a instância de `VsgDbg` não estiver gravando ativamente as informações gráficas, isso não terá efeito.

 Depois que `UnInit` tiver sido chamado em uma instância da classe `VsgDbg`, um novo arquivo de log de gráficos poderá ser criado chamando `Init` e finalizado chamando `UnInit`. Você pode repetir isso quantas vezes quiser usar a mesma instância de `VsgDbg` para criar vários arquivos de log de gráficos independentes.

## <a name="see-also"></a>Consulte também
- [Init](init.md)