---
title: SuspendTracking | Microsoft Docs
description: Aprenda a sintaxe, os requisitos e o valor de retorno para o MSBuild SuspendTracking, que suspende o rastreamento no contexto atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048085"
---
# <a name="suspendtracking"></a>SuspendTracking

Suspende o acompanhamento no contexto atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o bit com **êxito** definido se o rastreamento foi suspenso.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Veja também

- [ResumeTracking](../msbuild/resumetracking.md)