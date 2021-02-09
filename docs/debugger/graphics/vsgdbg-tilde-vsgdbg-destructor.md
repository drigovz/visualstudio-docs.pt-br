---
title: 'VsgDbg:: ~ VsgDbg (destruidor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 53d969e6be772b446598c9c3644582684be488a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861342"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruidor)
Destrói uma instância da `VsgDbg` classe. Se as informações gráficas estiverem sendo registradas ativamente, o arquivo de log de gráficos será finalizado e fechado, e os recursos que foram usados durante a captura ativa das informações gráficas serão liberados.

## <a name="syntax"></a>Sintaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Confira também
- [VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)