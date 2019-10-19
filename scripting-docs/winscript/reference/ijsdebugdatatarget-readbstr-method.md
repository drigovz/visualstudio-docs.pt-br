---
title: 'Método IJsDebugDataTarget:: ReadBSTR | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b125f58b4be279eac167b803ed6a683c1fb04ddf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572444"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>Método IJsDebugDataTarget::ReadBSTR
Lê um BSTR a partir do destino de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 no O endereço do qual ler.  
  
 `pString`  
 fora O BSTR lido do destino de depuração.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna E_JsDEBUG_INVALID_MEMORY_ADDRESS se o endereço não for válido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)