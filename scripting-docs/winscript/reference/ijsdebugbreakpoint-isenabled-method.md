---
title: 'Método ijsdebugbreakpoint:: IsEnabled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22584acafc92b7acaa09432ec9f6cb04e7bab48c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089369"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>Método IJsDebugBreakPoint::IsEnabled
Determina se o ponto de interrupção está habilitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIsEnabled`  
 [out] Retorna VERDADEIRO se o ponto de interrupção estiver habilitado; Caso contrário, retorna false.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará E_UNEXPECTED se chamado em um ponto de interrupção excluído.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)