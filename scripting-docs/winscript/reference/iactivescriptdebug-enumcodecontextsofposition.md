---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abca643dc4e18f786421959c20804a28cf54ec7b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097169"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Usado por um host inteligente para delegar a `IDebugDocumentContext::EnumCodeContexts` método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSourceContext`  
 [in] O contexto de origem conforme fornecido para `IActiveScriptParse::ParseScriptText` ou `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Caractere de deslocamento relativo ao início do texto do script.  
  
 `uNumChars`  
 [in] Número de caracteres nesse contexto.  
  
 `ppescc`  
 [out] Um enumerador dos contextos de código no intervalo especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Hosts inteligentes usam esse método para delegar a `IDebugDocumentContext::EnumCodeContexts` método.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)