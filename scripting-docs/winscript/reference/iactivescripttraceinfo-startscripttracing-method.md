---
title: 'Método iactivescripttraceinfo:: Startscripttracing | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b87971e1fd2e484aa54ff4de56ee56e00b19b1e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991190"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>Método IActiveScriptTraceInfo::StartScriptTracing
Inicia o rastreamento de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSiteTraceInfo`  
 Um ponteiro para IActiveScriptSiteTraceInfo do host.  
  
 `guidContextId`  
 O GUID do contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 Os valores de retornados possíveis para esse método são as seguintes:  
  
1. S_OK: Êxito.  
  
2. E_POINTER: `pSiteTraceInfo` é um ponteiro nulo.  
  
3. E_NOTIMPL: Não implementado.