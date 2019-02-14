---
title: ResumeTracking | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- ResumeTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2328b318c00b214138cf70e505c1988f8f1afc6a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802196"
---
# <a name="resumetracking"></a>ResumeTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Retoma o acompanhamento no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Um <!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->HRESULT<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  --> com o conjunto de bits SUCCEEDED se o acompanhamento tiver sido retomado. <!-- TODO: review code entity reference <xref:assetId:///E_FAIL?qualifyHint=False&amp;autoUpgrade=True>  -->E_FAIL será retornado se não for possível continuar o acompanhamento porque o contexto não estava disponível.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [SuspendTracking](../msbuild/suspendtracking.md)
