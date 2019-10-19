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
ms.openlocfilehash: b4a635a802ae84b8e839159f5e2f1c4c461e05ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572021"
---
# <a name="ienumjsstackframes-interface"></a>Interface IEnumJsStackFrames
Implementado pelo depurador para fornecer desenrolamento de pilha para jscript9diag. dll para JavaScript.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Name|Descrição|  
|----------|-----------------|  
|[IEnumJsStackFrames::Next Method](../../winscript/reference/ienumjsstackframes-next-method.md)|Obtém o número especificado de quadros.|  
|[IEnumJsStackFrames::Reset Method](../../winscript/reference/ienumjsstackframes-reset-method.md)|Redefine o quadro de pilhas para a posição anterior ao primeiro elemento.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)