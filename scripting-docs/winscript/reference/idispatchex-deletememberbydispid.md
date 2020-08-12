---
title: IDispatchEx::D eleteMemberByDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c3dbb040e39fd15b77e42b2eaa9fb2cdda0b1b2
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144630"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Exclui um membro por DISPID.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>parâmetros  
 `id`  
 Identificador de membro. Usa `GetDispID` ou `GetNextDispID` para obter o identificador de expedição.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor|Significado|
|-|-|  
|`S_OK`|Êxito.|  
|`S_FALSE`|O membro existe, mas não pode ser excluído.|  
  
## <a name="remarks"></a>Comentários  
 Se o membro for excluído, o DISPID precisa permanecer válido para `GetNextDispID` .  
  
 Se um membro com um determinado nome for excluído e posteriormente um membro com o mesmo nome for recriado, o DISPID deverá ser o mesmo. (Se os nomes de membros que diferem apenas em maiúsculas e minúsculas são os "mesmos" dependentes do objeto.)  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>Confira também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: getdispid](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)