---
title: Método IActiveScriptProfilerControl3::EnumHeap | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6120b8fdd913b4acee2e3ee6774d770aa75b1f5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992956"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>Método IActiveScriptProfilerControl3::EnumHeap
Retorna uma interface ([IActiveScriptProfilerHeapEnum Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) que pode ser usado para iterar sobre os objetos de heap de GC no contexto do mecanismo de script associado.  
  
 Você pode chamar esse método em depuração ou modo de versão. Esse método deve ser chamado quando o thread de interface do usuário está ocioso. Depois que o método foi chamado, nenhuma operação deve ser executada no mecanismo de script, exceto [método iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) até que [método iactivescriptprofilerheapenum:: Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)retorna S_FALSE ou o [IActiveScriptProfilerHeapEnum Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) ponteiro de interface é liberado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ppEnum  
 [out] Retorna o [Interface IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valor de retorno  
 O HRESULT.