---
title: 'IActiveScript:: SetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575326"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informa o mecanismo de script do site de interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fornecido pelo host. Chame esse método antes que quaisquer outros métodos de interface [IActiveScript](../../winscript/reference/iactivescript.md) sejam usados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pScriptSite`  
 no Endereço do site de script fornecido pelo host a ser associado a esta instância do mecanismo de script. O site deve ser atribuído exclusivamente a essa instância do mecanismo de script; Ele não pode ser compartilhado com outros mecanismos de script.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_FAIL`|Ocorreu um erro não especificado; o mecanismo de script não pôde concluir a inicialização do site.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, um site já foi definido).|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)