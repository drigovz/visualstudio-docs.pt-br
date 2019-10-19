---
title: Enumeração JsDebugReadMemoryFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571702"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumeração JsDebugReadMemoryFlags
Sinaliza para especificar o comportamento ao ler a memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Name|Descrição|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica que o chamador deseja que a operação de leitura tenha êxito se apenas parte da leitura da memória for bem-sucedida. Se estiver definido, um erro E_JsDEBUG_INVALID_MEMORY_ADDRESS será gerado somente se ' address ' for inválido. Se esse sinalizador estiver claro, um erro E_JsDEBUG_INVALID_MEMORY_ADDRESS será gerado se qualquer parte da memória solicitada não puder ser lida.|  
|`None`|Indica que o chamador deseja o comportamento padrão para ReadMemory.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)