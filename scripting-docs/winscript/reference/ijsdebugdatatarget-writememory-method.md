---
title: 'Método ijsdebugdatatarget:: Writememory | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 622de16cc5f755c5d69059a0e0f28d881121861c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558171"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>Método IJsDebugDataTarget::WriteMemory
Lê a memória do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] O endereço base da qual gravar a memória do processo de destino.  
  
 `pMemory`  
 [in] Os dados a serem gravados no espaço de endereço do processo especificado.  
  
 `size`  
 [in] O número de bytes a serem gravados no processo.  
  
## <a name="return-value"></a>Valor de retorno  
  
## <a name="remarks"></a>Comentários  
 Antes que ocorra a transferência de dados, o sistema verifica se todos os dados no endereço básico e a memória do tamanho especificado estão acessíveis para acesso de gravação e se não estiver acessível, a função gerará um erro de E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)