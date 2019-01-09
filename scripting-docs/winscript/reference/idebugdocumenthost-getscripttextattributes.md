---
title: 'Idebugdocumenthost:: Getscripttextattributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 016073d2ce22ab814716efc204ce573ea17cd510
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092710"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Retorna os atributos de texto de um bloco de texto do documento.  
  
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
 [in] O texto do bloco de script. Essa cadeia de caracteres não precisa ser terminado em null.  
  
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
|`E_NOTIMPL`|O host usa somente os atributos padrão.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna os atributos de texto para um bloco arbitrário de texto do documento. É aceitável para os hosts retornar `E_NOTIMPL`, caso em que os atributos padrão são usados.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)