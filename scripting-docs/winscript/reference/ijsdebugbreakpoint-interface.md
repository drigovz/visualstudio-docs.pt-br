---
title: Interface IJsDebugBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c43d23d0ba89e6b85a3dd4da688fa89fed4dd99
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093841"
---
# <a name="ijsdebugbreakpoint-interface"></a>Interface IJsDebugBreakPoint
Representa um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método IJsDebugBreakPoint::Delete](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|Exclui o ponto de interrupção.|  
|[Método IJsDebugBreakPoint::Disable](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|Desabilita o ponto de interrupção.|  
|[Método IJsDebugBreakPoint::Enable](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|Permite que o ponto de interrupção.|  
|[Método IJsDebugBreakPoint::GetDocumentPosition](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|Retorna a posição da instrução onde o ponto de interrupção foi associado.|  
|[Método IJsDebugBreakPoint::IsEnabled](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|Determina se o ponto de interrupção está habilitado.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)