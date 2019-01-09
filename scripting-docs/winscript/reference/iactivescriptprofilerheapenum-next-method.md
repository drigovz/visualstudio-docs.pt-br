---
title: 'Método iactivescriptprofilerheapenum:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1f8d709c98efba8551ffdd026b77234785c8de4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095726"
---
# <a name="iactivescriptprofilerheapenumnext-method"></a>Método IActiveScriptProfilerHeapEnum::Next
Obtém o próximo objeto ou objetos no conjunto de objetos de heap do [método IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Next (    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,     [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 O número de objetos a serem retornados.  
  
 `heapObjects`  
 [out] A próxima [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) estruturas.  
  
 `pceltFetched`  
 [out] O número de objetos retornados,  
  
## <a name="return-value"></a>Valor de retorno  
 O HRESULT.