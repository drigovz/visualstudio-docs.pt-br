---
title: IActiveScriptAuthor::P arseScriptText | Microsoft Docs
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
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576147"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analisa o texto do script, adiciona o texto ao mecanismo de criação de scripts e cria um `IScriptEntry` objeto que corresponde ao bloco de script.  
  
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
 no O texto do script a ser analisado.  
  
 `pszItemName`  
 no O endereço de buffer que contém o nome do item associado ao bloco de script.  
  
 `pszDelimiter`  
 no O endereço do delimitador de bloco de fim do script. Quando `pszCode` é analisada a partir de um fluxo de texto, o host normalmente usa um delimitador (como duas aspas simples) para detectar o final do bloco de script. Defina esse parâmetro como NULL se não houver nenhum delimitador para identificar o final do bloco de script.  
  
 `dwCookie`  
 no Um valor definido pelo aplicativo que está associado ao novo objeto `IScriptEntry`.  
  
 `dwFlags`  
 no Não usado.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthor Interface](../../winscript/reference/iactivescriptauthor-interface.md)