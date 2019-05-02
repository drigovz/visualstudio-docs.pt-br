---
title: 'Método ijsdebugbreakpoint:: Disable | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24584d0e9708dab4879ceb26f0af5e142936210a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583237"
---
# <a name="ijsdebugbreakpointdisable-method"></a>Método IJsDebugBreakPoint::Disable
Desabilita o ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará E_UNEXPECTED se chamado em um ponto de interrupção excluído. Retornará S_FALSE se chamado em um ponto de interrupção já desabilitado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)