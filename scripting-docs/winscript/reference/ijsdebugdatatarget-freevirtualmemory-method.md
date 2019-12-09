---
title: 'Método IJsDebugDataTarget:: FreeVirtualMemory | Microsoft Docs'
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
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577615"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>Método IJsDebugDataTarget::FreeVirtualMemory
Libera e/ou desconfirma uma região de memória dentro do espaço de endereço virtual do processo de destino.  
  
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
 no Endereço no processo de destino em que a memória deve ser liberada.  
  
 `size`  
 no Número de bytes a serem desconfirmados. Para liberar uma região da memória, esse valor deve ser zero.  
  
 `freeType`  
 no Indica o tipo de operação livre a ser executada. Normalmente, isso é MEM_RELEASE (0x8000), que libera a região de páginas especificada. Após a operação, as páginas estão no estado livre. MEM_DECOMMIT (0x4000) pode ser usado em vez de desconfirmar as páginas sem liberá-las.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Para obter informações adicionais, consulte a API do Win32 do VirtualFree.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)