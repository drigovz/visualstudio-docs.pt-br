---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68e80da01a0ab1ad59bbb5bdb06c92c1a11a8ac1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182318"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicia um contexto de acompanhamento usando um arquivo de resposta especificando um marcador de raiz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `intermediateDirectory`  
 O diretório no qual deseja armazenar o log de acompanhamento.  
  
 [in] `taskName`  
 Identifica o contexto de acompanhamento. Esse nome é usado para criar o nome de arquivo de log.  
  
 [in] `rootMarkerResponseFile`  
 O nome do caminho de um arquivo de resposta que contém um marcador de raiz. O nome da raiz é usado para agrupar todos os acompanhamentos para um contexto.  
  
## <a name="return-value"></a>Valor Retornado  
 Um [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) com [êxito] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits se o contexto de rastreamento foi criado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte Também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
