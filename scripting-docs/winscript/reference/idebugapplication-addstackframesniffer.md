---
title: IDebugApplication::AddStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddStackFrameSniffer
ms.assetid: a7a9684a-14c5-415a-ae63-a17397d58d07
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16fb941a91482c548284dc3d4317a472fd9be641
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145896"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Adiciona um provedor de enumerador de quadro de pilha para esse aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdsfs`  
 [in] O provedor de enumerador de quadro de pilha para adicionar a este aplicativo.  
  
 `pdwCookie`  
 [out] Um cookie que é usado para remover este provedor de enumerador de quadro de pilha do aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Embora os mecanismos de linguagem normalmente chama esse método para expor os quadros de pilhas do depurador, é possível que outras entidades para expor os quadros de pilha.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)   
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)