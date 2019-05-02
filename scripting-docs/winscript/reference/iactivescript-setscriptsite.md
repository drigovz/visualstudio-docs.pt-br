---
title: IActiveScript::SetScriptSite | Microsoft Docs
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
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935548"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informa ao mecanismo de script da [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) site interface fornecida pelo host. Chame esse método antes de qualquer outro [IActiveScript](../../winscript/reference/iactivescript.md) métodos de interface é usada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pScriptSite`  
 [in] Endereço do site do script fornecido pelo host a ser associado esta instância do mecanismo de script. O site deve ser atribuído exclusivamente a essa instância do mecanismo de script; ele não pode ser compartilhado com outros mecanismos de script.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_FAIL`|Ocorreu um erro não especificado; o mecanismo de script não pôde concluir a inicializar o site.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, um site já foi definido).|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)