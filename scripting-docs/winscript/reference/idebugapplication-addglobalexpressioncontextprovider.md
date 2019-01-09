---
title: IDebugApplication::AddGlobalExpressionContextProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.AddGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::AddGlobalExpressionContextProvider
ms.assetid: 35db7124-6970-4e45-8f00-ecdf21e9f5cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a17e952ef48041d8354753d27d7c40fef4599d55
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086821"
---
# <a name="idebugapplicationaddglobalexpressioncontextprovider"></a>IDebugApplication::AddGlobalExpressionContextProvider
Adiciona um provedor de contexto de expressão global para este aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddGlobalExpressionContextProvider(  
   IProvideExpressionContexts*  pdsfs,  
   DWORD_PTR*                   pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdsfs`  
 [in] O provedor de contexto global a ser adicionado a este aplicativo.  
  
 `pdwCookie`  
 [out] Um cookie que é usado para remover este provedor de contexto de expressão global do aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método adiciona um provedor de contexto de expressão global para este aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)