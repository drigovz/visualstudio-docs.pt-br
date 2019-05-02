---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
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
ms.openlocfilehash: 64df7bd4c0d0dde303cdc15d7111688d14c7dc49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935452"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Adiciona um scriptlet de código como um filho do nível raiz `IScriptNode` objeto. No host, o nome totalmente qualificado do scriptlet tem permissão para ter apenas dois níveis.  
  
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
 [in] O endereço do nome padrão para associar o scriptlet.  
  
 `pszCode`  
 [in] O endereço do texto de scriptlet.  
  
 `pszItemName`  
 [in] O endereço do buffer do identificador de nível superior do nome totalmente qualificado de scriptlet no host.  
  
 `pszSubItemName`  
 [in] O endereço do buffer do identificador do nome totalmente qualificado de scriptlet no host do segundo nível. Definido como NULL se o nome tem apenas um nível.  
  
 `pszEventName`  
 [in] O endereço de um buffer que contém o nome do evento para o qual o scriptlet é um manipulador de eventos.  
  
 `pszDelimiter`  
 [in] O endereço do delimitador de fim do bloco de script. Quando `pszCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador (como duas aspas simples), para detectar o fim do bloco de script. Defina esse parâmetro como NULL se um delimitador não marca o final do bloco de script.  
  
 `dwCookie`  
 [in] Um valor definido pelo aplicativo que é usado para associar o scriptlet com um objeto de host.  
  
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