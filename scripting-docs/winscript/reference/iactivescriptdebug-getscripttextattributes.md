---
title: IActiveScriptDebug::GetScriptTextAttributes | Microsoft Docs
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
ms.openlocfilehash: faec7cf65bed39a038c5ab7cc09d9908063a2c63
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009539"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Retorna os atributos de texto de um bloco arbitrário de texto de script.  
  
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
 [in] O texto do bloco de script. Essa cadeia de caracteres não precisa ser finalizada com null.  
  
 `uNumCodeChars`  
 [in] O número de caracteres no texto do bloco de script.  
  
 `pstrDelimiter`  
 [in] Endereço do delimitador de fim do bloco de script. Quando `pstrCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador, como duas aspas ("), para detectar o fim do bloco de script. Esse parâmetro especifica o delimitador que o host usou, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações dependem o mecanismo de script. Defina esse parâmetro como NULL se o host não usou um delimitador para marcar o fim do bloco de script.  
  
 `dwFlags`  
 [in] Sinalizadores associados com o bloco de script. Pode ser uma combinação desses valores:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica que identificadores e operadores dot devem ser identificados com os sinalizadores SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP, respectivamente.|  
|GETATTRFLAG_THIS|0x0100|Indica que o identificador para o objeto atual deve ser identificado com o sinalizador SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica que o texto de comentário e conteúdo de cadeia de caracteres deve ser identificado com o sinalizador SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [no, out] Buffer que conterá os atributos retornados.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um host inteligente que implementa `IDebugDocumentText` interface pode usar esse método para delegar a chamadas para o `IDebugDocumentText::GetText` método.  
  
 Esse método para blocos de script; o `GetScriptletTextAttributes` método destina-se miniscripts.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)