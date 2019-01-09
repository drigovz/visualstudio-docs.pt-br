---
title: IDebugStackFrame::GetLanguageString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: cc20c3ce2f5d198e167b83ffddb65cedc84402d7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087731"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Retorna uma descrição curta ou longa textual da linguagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fLong`  
 [in] Sinalizador, onde `TRUE` retorna uma descrição longa e `FALSE` retorna uma breve descrição.  
  
 `pbstrLanguage`  
 [out] A descrição da linguagem.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, se `fLong` é `FALSE`, esse método fornece apenas o nome do idioma associado ao quadro de pilha. Quando `fLong` é `TRUE`, esse método pode fornecer uma descrição completa do produto.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)