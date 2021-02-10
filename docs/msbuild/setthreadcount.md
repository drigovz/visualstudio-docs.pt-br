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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966156"
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