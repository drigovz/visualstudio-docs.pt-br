---
title: 'IScriptEntry:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c99cda48a20efb41b2535645ccdb50be8bb6d6bc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575443"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
Para entradas que representam um único objeto (como uma função), retorna o nome do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstr`  
 fora O nome do objeto representado pelo bloco de script `IScriptEntry`. Se uma entrada não representar um único objeto, NULL será retornado.  
  
 As entradas filho representam um único objeto de função.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IScriptEntry](../../winscript/reference/iscriptentry-interface.md)  
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)