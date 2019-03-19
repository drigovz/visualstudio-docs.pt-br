---
title: 'Método iactivescriptprofilerheapenum:: Getoptionalinfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8096b79cfbb91e4b65256c84ab1ba01207d9ed
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146988"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>Método IActiveScriptProfilerHeapEnum::GetOptionalInfo
Obtém informações opcionais no objeto especificado (o conjunto de objetos de heap retornados do [método IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Você não deve liberar a memória retornada atribuída para os objetos retornados. Em vez disso, você deve chamar o [método iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `heapObject`  
 O [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) para o qual retornar as informações.  
  
 `celt`  
 O número de [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) estruturas para retornar.  
  
 `optionalInfo`  
 [out] Uma matriz de [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) estruturas para o objeto especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 O HRESULT.