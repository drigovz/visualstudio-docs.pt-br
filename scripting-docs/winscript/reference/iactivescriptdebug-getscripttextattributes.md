---
title: 'IActiveScriptDebug:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576928"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Retorna os atributos de texto para um bloco de texto de script arbitrário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrCode`  
 no O texto do bloco de script. Essa cadeia de caracteres não precisa ser terminada em nulo.  
  
 `uNumCodeChars`  
 no O número de caracteres no texto do bloco de script.  
  
 `pstrDelimiter`  
 no Endereço do delimitador de bloco de fim do script. Quando `pstrCode` é analisada a partir de um fluxo de texto, o host geralmente usa um delimitador, como duas aspas simples (' '), para detectar o final do bloco de script. Esse parâmetro especifica o delimitador usado pelo host, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações depende do mecanismo de script. Defina esse parâmetro como NULL se o host não tiver usado um delimitador para marcar o final do bloco de script.  
  
 `dwFlags`  
 no Sinalizadores associados ao bloco de script. Pode ser uma combinação desses valores:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica que os identificadores e operadores de ponto devem ser identificados com os sinalizadores SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP, respectivamente.|  
|GETATTRFLAG_THIS|0x0100|Indica que o identificador do objeto atual deve ser identificado com o sinalizador SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica que o conteúdo da cadeia de caracteres e o texto do comentário devem ser identificados com o sinalizador SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [entrada, saída] Buffer para conter os atributos retornados.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um host inteligente que implementa `IDebugDocumentText` interface pode usar esse método para delegar chamadas para o método `IDebugDocumentText::GetText`.  
  
 Este método para blocos de script; o método `GetScriptletTextAttributes` é para scriptlets.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IActiveScriptDebug:: GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)    
 @No__t_1 de [interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
 [IDebugDocumentText:: gettext](../../winscript/reference/idebugdocumenttext-gettext.md)    
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)