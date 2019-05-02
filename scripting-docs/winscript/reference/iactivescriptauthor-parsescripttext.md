---
title: IActiveScriptAuthor::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe6870f3b19c5727fdbea0418b8373b990cb671a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955051"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analisa o texto do script, adiciona o texto para o mecanismo de criação de script e cria um `IScriptEntry` objeto que corresponde ao bloco de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCode`  
 [in] O texto do script para analisar.  
  
 `pszItemName`  
 [in] O endereço do buffer que contém o nome do item associado com o bloco de script.  
  
 `pszDelimiter`  
 [in] O endereço do delimitador de fim do bloco de script. Quando `pszCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador (como duas aspas simples), para detectar o fim do bloco de script. Defina esse parâmetro como NULL se não houver nenhum delimitador para identificar o fim do bloco de script.  
  
 `dwCookie`  
 [in] Um valor definido pelo aplicativo que está associado com o novo `IScriptEntry` objeto.  
  
 `dwFlags`  
 [in] Não usado.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthor Interface](../../winscript/reference/iactivescriptauthor-interface.md)