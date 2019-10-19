---
title: 'IActiveScriptAuthor:: GetScriptletTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576179"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Retorna os atributos de texto de um Scriptlet.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCode`  
 [in, size_is (`cch`)] O texto do scriptlet. Essa cadeia de caracteres não precisa ser terminada em nulo.  
  
 `cch`  
 no O tamanho usado para os parâmetros `pszCode` e `pattr`.  
  
 `pszDelimiter`  
 no O endereço do delimitador de fim do scriptlet. Quando `pszCode` é analisada a partir de um fluxo de texto, o host geralmente usa um delimitador (como duas aspas simples) para detectar o final do scriptlet. Defina esse parâmetro como NULL se nenhum delimitador for usado para identificar o final do scriptlet.  
  
 `dwFlags`  
 no Os sinalizadores associados aos atributos de texto do scriptlet. Pode ser uma combinação dos valores a seguir.  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identifique os identificadores que têm o atributo SOURCETEXT_ATTR_IDENTIFIER e identifique os operadores de ponto que têm o atributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identifique o objeto atual que tem o atributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identifique o conteúdo da cadeia de caracteres e o texto do comentário que tem o atributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] As informações de cor para o código de scriptlet.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor:: GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)    
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)