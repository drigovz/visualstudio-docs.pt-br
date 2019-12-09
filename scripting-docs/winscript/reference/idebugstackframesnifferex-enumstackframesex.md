---
title: 'IDebugStackFrameSnifferEx:: EnumStackFramesEx | Microsoft Docs'
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
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576706"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
Retorna um enumerador de quadros de pilhas para o thread atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSpMin`  
 no O limite de endereço inferior para enumerar os quadros de pilha.  
  
 `ppedsf`  
 fora Enumerador de quadros de pilha para o thread atual.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O enumerador de quadros de pilhas retorna os quadros que começam na parte superior da pilha, com o quadro enviado por push mais recentemente. O enumerador contém apenas quadros de pilha com endereços maiores ou iguais a `dwSpMin`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrameSnifferEx](../../winscript/reference/idebugstackframesnifferex-interface.md)