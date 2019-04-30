---
title: Interface IJsDebugStackWalker | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06af2c509339d9499f66e1f267c54c69951e225
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977806"
---
# <a name="ijsdebugstackwalker-interface"></a>Interface IJsDebugStackWalker
Representa um caminhador de pilha para um thread especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtém o próximo quadro.|  
  
## <a name="remarks"></a>Comentários  
 Os walkers de pilha só podem ser criados enquanto o destino for interrompido e serão inválido quando o processo de destino foi continuado novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)