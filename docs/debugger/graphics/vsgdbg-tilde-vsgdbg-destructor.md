---
title: 'VsgDbg:: ~ VsgDbg (destruidor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc518e649732f6774259efed0965a9898e0fb2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734794"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruidor)
Destrói uma instância da `VsgDbg` classe. Se as informações gráficas estiverem sendo registradas ativamente, o arquivo de log de gráficos será finalizado e fechado, e os recursos que foram usados durante a captura ativa das informações gráficas serão liberados.

## <a name="syntax"></a>Sintaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Confira também
- [VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)