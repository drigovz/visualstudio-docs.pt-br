---
title: ResumeTracking | Microsoft Docs
description: Aprenda a sintaxe, os requisitos e o valor de retorno para o MSBuild ResumeTracking, que retoma o acompanhamento no contexto atual.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9af7c90342638fb0c154e7de21fa111d560905d0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048424"
---
# <a name="resumetracking"></a>ResumeTracking

Retoma o acompanhamento no contexto atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o bit com **êxito** definido se o controle foi retomado. **E_FAIL** será retornado se o rastreamento não puder ser retomado porque o contexto não estava disponível.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Veja também

- [SuspendTracking](../msbuild/suspendtracking.md)