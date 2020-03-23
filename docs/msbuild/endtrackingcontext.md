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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf982200b8e65e404325bdbd189ff3b0f2daebac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634234"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Finaliza o contexto atual de acompanhamento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Valor retornado

Um **HRESULT** com o **conjunto de bits BEM SUCEDIDO** se o contexto de rastreamento foi encerrado.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Confira também

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
