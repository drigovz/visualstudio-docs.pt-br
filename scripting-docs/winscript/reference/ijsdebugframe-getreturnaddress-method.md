---
title: 'Método IJsDebugFrame:: GetReturnAddress | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 802355bdef386ceb252e776f8c6e798df18c9253
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577357"
---
# <a name="ijsdebugframegetreturnaddress-method"></a>Método IJsDebugFrame::GetReturnAddress
Obtém o endereço de retorno enviado por push no ' Start ' (consulte GetStackRange) do quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pReturnAddress`  
 fora O endereço de retorno.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)