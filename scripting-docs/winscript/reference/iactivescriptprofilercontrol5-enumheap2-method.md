---
title: Método IActiveScriptProfilerControl5::EnumHeap2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c90c536dee76d67fdb93dd205e8f6eedff6dcc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992933"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>Método IActiveScriptProfilerControl5::EnumHeap2
Retorna uma interface ([IActiveScriptProfilerHeapEnum Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que pode ser usado para iterar sobre os objetos de heap de GC no contexto do mecanismo de script associado.  
  
 Você pode chamar esse método em depuração ou modo de versão. Esse método deve ser chamado quando o thread de interface do usuário está ocioso. Depois que o método foi chamado, nenhuma operação deve ser executada no mecanismo de script, exceto [método iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) até que [método iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)retorna S_FALSE ou o [IActiveScriptProfilerHeapEnum Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) ponteiro de interface é liberado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 enumFlags  
 Valor que especifica se as informações adicionais sobre um objeto apontado em uma relação de objeto são expostas. Informações adicionais podem indicar se o objeto apontado é um método getter ou setter. Para obter mais informações, consulte [enumeração PROFILER_HEAP_ENUM_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Retorna o [Interface IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um HRESULT. Os valores possíveis são:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|A enumeração de heap foi concluída com êxito.|  
|`E_OUTOFMEMORY`|Não havia memória suficiente disponível para executar a enumeração de heap.|  
|`E_FAIL`|Ocorreu um erro interno.|