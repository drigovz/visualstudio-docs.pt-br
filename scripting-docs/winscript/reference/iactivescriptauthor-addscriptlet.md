---
title: 'IActiveScriptAuthor:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577979"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Adiciona um Scriptlet de código como um filho do nível raiz `IScriptNode` objeto. No host, o nome totalmente qualificado do scriptlet tem permissão para ter apenas dois níveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszDefaultName`  
 no O endereço do nome padrão a ser associado ao scriptlet.  
  
 `pszCode`  
 no O endereço do texto do scriptlet.  
  
 `pszItemName`  
 no O endereço de buffer do identificador de nível superior do nome do scriptlet totalmente qualificado no host.  
  
 `pszSubItemName`  
 no O endereço de buffer do identificador de segundo nível do nome totalmente qualificado do scriptlet no host. Defina como NULL se o nome tiver apenas um nível.  
  
 `pszEventName`  
 no O endereço de um buffer que contém o nome do evento para o qual o scriptlet é um manipulador de eventos.  
  
 `pszDelimiter`  
 no O endereço do delimitador de bloco de fim do script. Quando `pszCode` é analisada a partir de um fluxo de texto, o host normalmente usa um delimitador (como duas aspas simples) para detectar o final do bloco de script. Defina esse parâmetro como NULL se um delimitador não marcar o final do bloco de script.  
  
 `dwCookie`  
 no Um valor definido pelo aplicativo que é usado para associar o scriptlet a um objeto de host.  
  
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