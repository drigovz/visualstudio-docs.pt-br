---
title: Interface IJsDebugStackWalker | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d79950c6d5595a0a8a95623a7510c5523f16e41b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087887"
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