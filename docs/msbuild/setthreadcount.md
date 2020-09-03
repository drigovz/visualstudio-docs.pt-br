---
title: SetThreadCount | Microsoft Docs
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
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632323"
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