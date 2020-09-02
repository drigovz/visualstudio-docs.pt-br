---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da002fe757d623a665b39c16cc10e77e492e2660
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199930"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicie um contexto de acompanhamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `intermediateDirectory`  
 O diretório no qual deseja armazenar o log de acompanhamento.  
  
 [in] `taskName`  
 Identifica o contexto de acompanhamento. Esse nome é usado para criar o nome de arquivo de log.  
  
## <a name="return-value"></a>Valor Retornado  
 Um [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) com [êxito] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits se o contexto de rastreamento foi criado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h
