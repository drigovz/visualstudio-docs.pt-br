---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c395df1e08f1b4e33e9cd34fec54bdd044f3b4c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939203"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Inicie um contexto de acompanhamento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Parâmetros
[in] `intermediateDirectory`

 O diretório no qual deseja armazenar o log de acompanhamento.

[in] `taskName`

 Identifica o contexto de acompanhamento. Esse nome é usado para criar o nome de arquivo de log.

## <a name="return-value"></a>Valor retornado
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o contexto de acompanhamento foi criado.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *FileTracker.h*