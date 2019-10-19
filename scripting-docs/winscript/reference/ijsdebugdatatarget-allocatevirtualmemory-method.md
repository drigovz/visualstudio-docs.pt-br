---
title: 'Método IJsDebugDataTarget:: AllocateVirtualMemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577639"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Método IJsDebugDataTarget::AllocateVirtualMemory
Reserva e/ou confirma uma região de memória dentro do espaço de endereço virtual do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 no O endereço no processo de destino em que a memória deve ser confirmada ou reservada. Esse valor geralmente é zero; nesse caso, o sistema escolhe um endereço.  
  
 `size`  
 no O tamanho da região de memória a ser alocada, em bytes. O sistema será arredondado automaticamente para o próximo limite de página.  
  
 `allocationType`  
 no Indica o tipo de alocação a ser executado. Normalmente, isso é &#124; MEM_COMMIT MEM_RESERVE (0x3000) que reserva e confirma uma alocação em uma única etapa.  
  
 `pageProtection`  
 no A proteção de memória para a região de páginas a ser alocada. Se as páginas estiverem sendo confirmadas, você poderá especificar qualquer uma das constantes de proteção de memória (por exemplo, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 fora Endereço base da região de páginas alocada.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 A função inicializa a memória alocada para zero, a menos que MEM_RESET seja usado. Para obter informações adicionais, consulte a API do Win32 do VirtualAlloc.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)