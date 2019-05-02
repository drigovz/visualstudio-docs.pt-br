---
title: 'Método ijsdebugdatatarget:: Readmemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 705fff3bf2d4be78897c18c5a4c61bd74a8c2230
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582349"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>Método IJsDebugDataTarget::ReadMemory
Lê a memória do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] O endereço base do qual ler a memória do processo de destino.  
  
 `flags`  
 [in] Sinalizadores de controlar o comportamento de ReadMemory.  
  
 `pBuffer`  
 [out] Um buffer que recebe o conteúdo do espaço de endereço do processo de destino. Em caso de falha, o conteúdo desse buffer é especificado.  
  
 `size`  
 [in] O número de bytes a serem lidos do processo.  
  
 `pBytesRead`  
 [out] Indica o número de bytes lidos do processo de destino. Se JsDebugAllowPartialRead estiver desmarcado, em caso de sucesso esse valor sempre será exatamente igual ao tamanho de entrada. Se JsDebugAllowPartialRead estiver especificado, em caso de sucesso, esse valor será maior que zero.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Retorna S_OK no êxito e códigos de falha é usada para qualquer erro. Retornará E_JsDEBUG_INVALID_MEMORY_ADDRESS se o endereço não é válido. Para obter mais informações, consulte JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)