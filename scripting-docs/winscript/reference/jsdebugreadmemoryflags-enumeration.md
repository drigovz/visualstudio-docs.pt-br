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
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830456"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumeração JsDebugReadMemoryFlags
Sinaliza para especificar o comportamento ao ler a memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="values"></a>Valores  
  
|Nome|Descrição|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica que o chamador deseja que a operação de leitura seja bem-sucedida somente se parte da memória ler com êxito. Se isso estiver definido, um erro E_JsDEBUG_INVALID_MEMORY_ADDRESS só será gerado se 'Endereço' é inválido. Se esse sinalizador estiver desmarcado, um erro E_JsDEBUG_INVALID_MEMORY_ADDRESS será gerado se qualquer parte de memória esteja ilegível.|  
|`None`|Indica que o chamador deseja o comportamento padrão para ReadMemory.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)