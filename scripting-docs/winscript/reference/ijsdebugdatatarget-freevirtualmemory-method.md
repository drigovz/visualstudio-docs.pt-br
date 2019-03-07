---
title: 'Método ijsdebugdatatarget:: Freevirtualmemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed5fabfca8ac9b0e9fe0dfba346b0354f4c0576f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086795"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Método IJsDebugDataTarget::FreeVirtualMemory
Libera e/ou anulações de confirmação de uma região de memória no espaço de endereço virtual do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Endereço dentro do processo de destino em que a memória deve ser liberada.  
  
 `size`  
 [in] Número de bytes a serem anulados. Para definir uma região de memória, esse valor deve ser zero.  
  
 `freeType`  
 [in] Indica o tipo de operação livre a ser executada. Isso geralmente é MEM_RELEASE (0x8000), que libera a região especificada de páginas. Após a operação, as páginas estão em estado livre. MEM_DECOMMIT (0x4000) pode ser usado em vez disso, a serem anulados as páginas sem liberá-los.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações, consulte a API Win32 VirtualFree.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)