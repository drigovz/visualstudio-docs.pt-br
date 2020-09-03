---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632089"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Inicia um contexto de acompanhamento usando um arquivo de resposta especificando um marcador de raiz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parâmetros

[in] `intermediateDirectory`

 O diretório no qual deseja armazenar o log de acompanhamento.

[in] `taskName`

 Identifica o contexto de acompanhamento. Esse nome é usado para criar o nome de arquivo de log.

[in] `rootMarkerResponseFile`

 O nome do caminho de um arquivo de resposta que contém um marcador de raiz. O nome da raiz é usado para agrupar todos os acompanhamentos para um contexto.

## <a name="return-value"></a>Valor retornado

 Um **HRESULT** com o bit com **êxito** definido se o contexto de rastreamento foi criado.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Confira também

- [StartTrackingContext](../msbuild/starttrackingcontext.md)