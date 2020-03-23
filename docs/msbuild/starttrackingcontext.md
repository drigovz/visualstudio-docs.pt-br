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
ms.openlocfilehash: 50f62704897d68b0e323b948b8f4ed7e96a10c9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632102"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Inicie um contexto de acompanhamento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>parâmetros

[in] `intermediateDirectory`

 O diretório no qual deseja armazenar o log de acompanhamento.

[in] `taskName`

 Identifica o contexto de acompanhamento. Esse nome é usado para criar o nome de arquivo de log.

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o **conjunto de bits BEM SUCEDIDO** se o contexto de rastreamento foi criado.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*
