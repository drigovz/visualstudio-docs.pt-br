---
title: 'Método IJsDebugDataTarget:: WriteMemory | Microsoft Docs'
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
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572422"
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
 no O endereço base do qual gravar a memória do processo de destino.  
  
 `pMemory`  
 no Os dados a serem gravados no espaço de endereço do processo especificado.  
  
 `size`  
 no O número de bytes a serem gravados no processo.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="remarks"></a>Comentários  
 Antes que a transferência de dados ocorra, o sistema verifica se todos os dados no endereço base e a memória do tamanho especificado estão acessíveis para acesso de gravação e, se não estiver acessível, a função gerará um erro E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)