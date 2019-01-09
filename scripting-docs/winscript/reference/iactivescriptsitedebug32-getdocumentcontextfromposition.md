---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9a52abcfa4defb49526f944469c95a2247f5d85c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094478"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Usado pelo mecanismo de linguagem para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSourceContext`  
 [in] O conteúdo de origem conforme fornecido para `ParseScriptText` ou `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Caractere de deslocamento relativo ao início do bloco de script ou o scriptlet.  
  
 `uNumChars`  
 [in] Número de caracteres nesse contexto.  
  
 `ppsc`  
 [out] O contexto do documento correspondente a esse intervalo de posição do caractere.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Mecanismos de linguagem usam esse método para delegar `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebug32 Interface](../../winscript/reference/iactivescriptsitedebug32-interface.md)