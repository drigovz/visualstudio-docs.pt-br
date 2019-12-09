---
title: 'IActiveScriptAuthor:: RemoveNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572845"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Remove um objeto `NamedItem` do namespace do mecanismo de criação de scripts.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszName`  
 no O endereço do buffer que identifica o objeto de `NamedItem` a ser removido.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`S_FALSE`|O objeto `NamedItem` não está presente no namespace do mecanismo de criação de scripts.|  
  
## <a name="remarks"></a>Comentários  
 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) é usado para injetar o objeto `NamedItem` no namespace do mecanismo de criação de scripts.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)