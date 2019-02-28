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
ms.openlocfilehash: 64d2ce58a0a543a6bccfca4d96ff57915d45ce49
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686555"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruidor)
Destrói uma instância da `VsgDbg` classe. Se informações de gráficos ativamente está sendo registradas, o arquivo de log de gráficos é finalizado e fechado, e os recursos que foram usados durante a captura ativamente informações gráficas são liberados.

## <a name="syntax"></a>Sintaxe

```C++
~VsgDbg();
```

## <a name="see-also"></a>Consulte também
- [VsgDbg::VsgDbg (Construtor)](vsgdbg-vsgdbg-constructor.md)