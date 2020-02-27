---
title: ResumeTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632492"
---
# <a name="resumetracking"></a>ResumeTracking

Retoma o acompanhamento no contexto atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido retomado. **E_FAIL** será retornado se não for possível continuar o acompanhamento porque o contexto não estava disponível.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker. h*

## <a name="see-also"></a>Confira também

- [SuspendTracking](../msbuild/suspendtracking.md)