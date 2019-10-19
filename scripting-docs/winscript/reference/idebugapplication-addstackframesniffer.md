---
title: 'IDebugApplication:: AddStackFrameSniffer | Microsoft Docs'
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
ms.openlocfilehash: a461c24b6f62f1e0ece88915e097faf0c59f15e7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575029"
---
# <a name="idebugapplicationaddstackframesniffer"></a>IDebugApplication::AddStackFrameSniffer
Adiciona um provedor de enumerador de quadros de pilha a este aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddStackFrameSniffer(  
   IDebugStackFrameSniffer*  pdsfs,  
   DWORD*                    pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdsfs`  
 no O provedor de enumerador de quadros de pilha para adicionar a este aplicativo.  
  
 `pdwCookie`  
 fora Um cookie que é usado para remover esse provedor de enumerador de quadros do aplicativo.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Embora os mecanismos de linguagem normalmente chamem esse método para expor seus quadros de pilha para o depurador, é possível que outras entidades exponham os quadros de pilha.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugApplication:: RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)    
 [Interface IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)