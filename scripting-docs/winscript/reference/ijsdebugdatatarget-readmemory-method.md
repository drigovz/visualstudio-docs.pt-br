---
title: 'Método IJsDebugDataTarget:: ReadMemory | Microsoft Docs'
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
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572426"
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
 no O endereço base do qual ler a memória do processo de destino.  
  
 `flags`  
 no Sinalizadores que controlam o comportamento de ReadMemory.  
  
 `pBuffer`  
 fora Um buffer que recebe o conteúdo do espaço de endereço do processo de destino. Em caso de falha, o conteúdo desse buffer não é especificado.  
  
 `size`  
 no O número de bytes a serem lidos do processo.  
  
 `pBytesRead`  
 fora Indica o número de bytes lidos do processo de destino. Se JsDebugAllowPartialRead for clara, em caso de sucesso, esse valor será sempre exatamente igual ao tamanho de entrada. Se JsDebugAllowPartialRead for especificado, em caso de êxito, esse valor será maior que zero.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Retorna S_OK em caso de êxito e os códigos de falha são usados para qualquer erro. Retorna E_JsDEBUG_INVALID_MEMORY_ADDRESS se o endereço não for válido. Para obter mais informações, consulte JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)