---
title: 'IScriptEntry:: setitemname | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575363"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Define o nome do item que identifica um objeto de `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `psz`  
 no O endereço de um buffer que contém o nome do item. O nome do item é usado pelo host para identificar a entrada.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|O método não teve sucesso.|  
  
## <a name="remarks"></a>Comentários  
 Para objetos `IScriptEntry`, esse método retorna `S_OK`.  
  
 Para objetos `IScriptScriptlet` (que derivam de `IScriptEntry`), esse método retorna `E_FAIL`. Para objetos `IScriptScriptlet`, o nome do item é definido por [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) e não pode ser alterado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)