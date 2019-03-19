---
title: IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1984cdc19beb883dd7ee82f58497b11a8d781b0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144427"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Recupera o intervalo de caracteres e o mecanismo de script correspondente a um bloco de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSourceContext`  
 [in] O contexto de origem para o bloco de script.  
  
 `ppasd`  
 [out] O mecanismo de script para este bloco de script.  
  
 `piCharPos`  
 [out] Local do início do bloco de script.  
  
 `cChars`  
 [out] Número de caracteres no bloco de script.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera o intervalo de caracteres e o mecanismo de script correspondente a um bloco de script.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentHelper Interface](../../winscript/reference/idebugdocumenthelper-interface.md)