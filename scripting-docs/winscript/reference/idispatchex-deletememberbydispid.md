---
title: IDispatchEx::DeleteMemberByDispID | Microsoft Docs
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
ms.openlocfilehash: 38ead33fb51caff1103ca9abe6bc01f3e0aa6aa3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576647"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
Exclui um membro por DISPID.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `id`  
 Identificador de membro. Usa `GetDispID` ou `GetNextDispID` para obter o identificador de expedição.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|||  
|-|-|  
|`S_OK`|Êxito.|  
|`S_FALSE`|O membro existe, mas não pode ser excluído.|  
  
## <a name="remarks"></a>Comentários  
 Se o membro for excluído, o DISPID precisa permanecer válido por `GetNextDispID`.  
  
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
  
## <a name="see-also"></a>Consulte também  
   de [interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)