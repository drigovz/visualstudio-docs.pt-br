---
title: 'IDebugStackFrame:: getlanguagestring | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83abb038cd8bc018d84cd0c5ddd2a413f8a02248
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576755"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Retorna uma descrição textual curta ou longa do idioma.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fLong`  
 no Sinalizador, onde `TRUE` retorna uma descrição longa e `FALSE` retorna uma breve descrição.  
  
 `pbstrLanguage`  
 fora A descrição do idioma.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, se `fLong` for `FALSE`, esse método fornecerá apenas o nome do idioma associado ao quadro de pilha. Quando `fLong` é `TRUE`, esse método pode fornecer uma descrição completa do produto.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)