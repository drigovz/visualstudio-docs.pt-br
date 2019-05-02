---
title: IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8969c279e4eb2c2966e297317a25a60f12be68a9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005713"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Retorna um enumerador dos quadros de pilha do thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSpMin`  
 [in] O limite inferior de endereço para a enumeração dos quadros de pilha.  
  
 `ppedsf`  
 [out] Enumerador de quadros de pilha do thread atual.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O enumerador de quadro de pilha retorna os quadros começando do topo da pilha, com o quadro mais recentemente enviados por push. O enumerador contém somente os quadros de pilha com endereços maior que ou iguais a `dwSpMin`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)