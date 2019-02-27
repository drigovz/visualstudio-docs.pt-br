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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 656e491e683c7ec2de23ea7e49938e833af3a295
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709610"
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
 Um **HRESULT** com o conjunto de bit **SUCCEEDED** se a contagem de thread foi atualizada.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *FileTracker.h*