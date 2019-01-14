---
title: ResumeTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9608ca6237a44d48d4ee4c4d8daf057d88fc5b53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947823"
---
# <a name="resumetracking"></a>ResumeTracking
Retoma o acompanhamento no contexto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido retomado. **E_FAIL** será retornado se não for possível continuar o acompanhamento porque o contexto não estava disponível.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** *FileTracker.h*  
  
## <a name="see-also"></a>Consulte também  
 [SuspendTracking](../msbuild/suspendtracking.md)