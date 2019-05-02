---
title: IJsDebugBreakPoint Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14823baeb999ad24aabef9b2b55b59a7b5d08c71
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583100"
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