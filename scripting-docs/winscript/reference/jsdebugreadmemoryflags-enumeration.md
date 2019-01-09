---
title: Enumeração JsDebugReadMemoryFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef1f16ebcf678452f2fe4b0df3ade6350120f05
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094023"
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