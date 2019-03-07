---
title: 'IActiveScript:: Setscriptsite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b2a96732e904c7249dc5228ef414c3315012ec56
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097429"
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