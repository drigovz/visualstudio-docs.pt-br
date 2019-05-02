---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7f837e7a983d0f2c2520d7e379ffb49f332c75c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821111"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Finaliza o contexto atual de acompanhamento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valor retornado
Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o contexto de acompanhamento tiver sido finalizado.

## <a name="requirements"></a>Requisitos
**Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Consulte também
- [StartTrackingContext](../msbuild/starttrackingcontext.md)
