---
title: SuspendTracking | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- SuspendTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a72045e7e03a21bd827be1501251db823ca6ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782539"
---
# <a name="suspendtracking"></a>SuspendTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Suspende o acompanhamento no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Um [HRESULT](<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) com o conjunto de bits [SUCCEEDED](<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) se o acompanhamento foi suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [ResumeTracking](../msbuild/resumetracking.md)
