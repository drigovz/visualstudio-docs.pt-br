---
title: 'IScriptEntry:: setBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575376"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
Define o texto que está no corpo de um bloco de script `IScriptEntry` ou um Scriptlet `IScriptScriptlet`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `psz`  
 no Para um bloco de script `IScriptEntry`, `psz` é o texto incluído nas marcas de script.  
  
 Para um bloco de função `IScriptEntry`, `psz` é o corpo da função.  
  
 Para um objeto `IScriptScriptlet` (que deriva de `IScriptEntry`), `psz` é o texto do script do scriptlet.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)