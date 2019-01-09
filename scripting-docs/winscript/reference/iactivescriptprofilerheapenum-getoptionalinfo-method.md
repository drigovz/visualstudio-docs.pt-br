---
title: 'Método iactivescriptprofilerheapenum:: Getoptionalinfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcba1214a0c57e738dec41cdc4976f478802fedc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088797"
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