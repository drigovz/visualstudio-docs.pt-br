---
title: Interface IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e8302737fb4abf96c55d3ae70424cc03579b270
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963319"
---
# <a name="ienumjsstackframes-interface"></a>Interface IEnumJsStackFrames
Implementado pelo depurador para fornecer a pilha de desenrolamento para jscript9diag.dll para JavaScript.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next Method](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtém o número especificado de quadros.|  
|[IEnumJsStackFrames::Reset Method](../../winscript/reference/ienumjsstackframes-reset-method.md)|Redefine o quadro de pilha para a posição antes do primeiro elemento.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)