---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee30bf031761fa7920dadad04d8f17a1bcc0b3a2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631985"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Interrompe o acompanhamento e libera a memória usada pela sessão de acompanhamento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valor retornado

 Retorna um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido interrompido.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Confira também

- [StartTrackingContext](../msbuild/starttrackingcontext.md)