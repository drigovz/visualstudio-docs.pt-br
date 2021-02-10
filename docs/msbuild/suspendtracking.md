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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945273"
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

## <a name="see-also"></a>Consulte também

- [ResumeTracking](../msbuild/resumetracking.md)