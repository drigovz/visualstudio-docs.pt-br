---
title: 'Método ijsdebugdatatarget:: Freevirtualmemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583035"
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