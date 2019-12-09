---
title: 'IActiveScriptDebug:: EnumCodeContextsOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572776"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Usado por um host inteligente para delegar o método de `IDebugDocumentContext::EnumCodeContexts`.  
  
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
 no O contexto de origem fornecido para `IActiveScriptParse::ParseScriptText` ou `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 no Deslocamento de caractere relativo ao início do texto do script.  
  
 `uNumChars`  
 no Número de caracteres neste contexto.  
  
 `ppescc`  
 fora Um enumerador dos contextos de código no intervalo especificado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Os hosts inteligentes usam esse método para delegar o método de `IDebugDocumentContext::EnumCodeContexts`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)