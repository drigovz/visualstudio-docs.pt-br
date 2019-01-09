---
title: Interface IEnumJsStackFrames | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c26470e02f6c7e5d8911df7e743bce0cb0e560bb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087874"
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