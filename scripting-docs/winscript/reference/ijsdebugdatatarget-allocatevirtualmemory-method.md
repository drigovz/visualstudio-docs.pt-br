---
title: 'Método ijsdebugdatatarget:: Allocatevirtualmemory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4eaf448e0be224f853674084a18f7aa2a6bd5ed7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086900"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>Método IJsDebugDataTarget::AllocateVirtualMemory
Reserva e/ou confirma uma região de memória no espaço de endereço virtual do processo de destino.  
  
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
 [in] O endereço dentro do processo de destino em que a memória deve ser confirmada ou reservada. Normalmente, esse valor é zero, caso o sistema escolhe um endereço.  
  
 `size`  
 [in] O tamanho da região da memória para alocar, em bytes. O sistema irá arredondar automaticamente até o limite da próxima página.  
  
 `allocationType`  
 [in] Indica o tipo de alocação a ser executada. Isso geralmente é MEM_COMMIT &#124; MEM_RESERVE (0x3000), que reserva e confirma uma alocação em uma única etapa.  
  
 `pageProtection`  
 [in] A proteção de memória para a região das páginas a serem alocados. Se as páginas estiverem sendo confirmadas, você pode especificar qualquer uma das constantes de proteção de memória (por exemplo, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Endereço básico da região atribuída das páginas.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 A função inicializa a memória que aloca a zero, a menos que MEM_RESET seja usado. Para obter mais informações, consulte a API Win32 VirtualAlloc.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)