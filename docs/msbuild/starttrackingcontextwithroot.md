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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 721d50b4e710e19c759bb418197d82c4828e6961
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989994"
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
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o contexto de acompanhamento foi criado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** *FileTracker.h*  
  
## <a name="see-also"></a>Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)