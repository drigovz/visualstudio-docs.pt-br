---
title: 'Método ijsdebugdatatarget:: Readbstr | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: afd216c869cd88a643f68f0abd1fc095a675e24b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095791"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>Método IJsDebugDataTarget::ReadBSTR
Lê um BSTR do destino de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] O endereço de onde ler.  
  
 `pString`  
 [out] Leia o BSTR do destino de depuração.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retornará E_JsDEBUG_INVALID_MEMORY_ADDRESS se o endereço não é válido.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)