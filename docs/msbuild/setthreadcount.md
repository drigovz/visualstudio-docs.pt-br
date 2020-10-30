---
title: SetThreadCount | Microsoft Docs
description: Saiba como o MSBuild usa SetThreadCount para definir a contagem de threads globais e atribua essa contagem ao thread atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01bfdae1dcd11d7df042948308c424b7773b3bb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048325"
---
# <a name="setthreadcount"></a>SetThreadCount

Define a contagem de thread global e atribui valores para o thread atual.

## <a name="syntax"></a>Sintaxe

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parâmetros

[in] `threadCount`

 O número máximo de threads.

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o bit com **êxito** definido se a contagem de threads foi atualizada.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*