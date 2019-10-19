---
title: 'IActiveScriptAuthor:: GetRoot | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetRoot
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2aab154d56cd98c3c2acede61f86f725ce9c1b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576182"
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Retorna o `IScriptNode` raiz da árvore de script do autor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppsp`  
 fora O endereço de uma variável que recebe um ponteiro para a interface `IScriptNode` do nó raiz.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)