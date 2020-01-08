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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b84753974eeecb8dca85035d50635d0bee47645
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595040"
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

## <a name="requirements"></a>Requisitos do
 **Cabeçalho:** *FileTracker. h*
