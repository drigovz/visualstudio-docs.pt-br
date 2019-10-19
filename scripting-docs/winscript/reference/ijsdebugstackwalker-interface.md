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
ms.openlocfilehash: 3b06b8c1f9282c42599c798030440c30450ef6dd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574013"
---
# <a name="ijsdebugstackwalker-interface"></a>Interface IJsDebugStackWalker
Representa um Stack Walker para um thread especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IJsDebugStackWalker : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Name|Descrição|  
|----------|-----------------|  
|[Método IJsDebugStackWalker::GetNext](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Obtém o próximo quadro.|  
  
## <a name="remarks"></a>Comentários  
 Os analisadores de pilha só podem ser criados enquanto o destino é parado e são inválidos quando o processo de destino continua novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)