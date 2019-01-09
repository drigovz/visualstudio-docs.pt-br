---
title: 'Método ijsdebugframe:: Getreturnaddress | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetReturnAddress
apilocation:
- jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78384fc4e65dcd5e1f41f3f83b98c3fab5b12cfd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093893"
---
# <a name="ijsdebugframegetreturnaddress-method"></a>Método IJsDebugFrame::GetReturnAddress
Obtém o endereço de retorno enviado por push no 'Início' (consulte GetStackRange) do quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pReturnAddress`  
 [out] O endereço de retorno.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)