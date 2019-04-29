---
title: 'Método iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6023ca95b3e861b7bf57db3d37c7949e650419b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992874"
---
# <a name="iactivescriptprofilerheapenumfreeobjectandoptionalinfo-method"></a>Método IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo
Libera a especificada [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) estruturas e seus respectivos [estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT FreeObjectAndOptionalInfo (    [in] ULONG celt,    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 O número de objetos para liberar.  
  
 `heapObjects`  
 Uma matriz de [estrutura PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) estruturas.  
  
## <a name="return-value"></a>Valor de retorno  
 O HRESULT.