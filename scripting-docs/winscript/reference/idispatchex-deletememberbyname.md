---
title: IDispatchEx::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576619"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Exclui um membro por nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bstrName`  
 Nome do membro a ser excluído.  
  
 `grfdex`  
 Determina se o nome do membro diferencia maiúsculas de minúsculas. Isso pode ser um dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicita que a pesquisa de nome seja feita de maneira diferenciada de maiúsculas e minúsculas. Pode ser ignorado por um objeto que não dá suporte à pesquisa que diferencia maiúsculas de minúsculas.|  
|fdexNameCaseInsensitive|Solicita que a pesquisa de nome seja feita de maneira não diferencia maiúsculas de minúsculas. Pode ser ignorado por um objeto que não dá suporte à pesquisa que não diferencia maiúsculas de minúsculas.|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|||  
|-|-|  
|`S_OK`|Êxito.|  
|`S_FALSE`|O membro existe, mas não pode ser excluído.|  
  
## <a name="remarks"></a>Comentários  
 Se o membro for excluído, o DISPID precisa permanecer válido por `GetNextDispID`.  
  
 Se um membro com um determinado nome for excluído e posteriormente um membro com o mesmo nome for recriado, o DISPID deverá ser o mesmo. (Se os membros que diferem apenas em maiúsculas e minúsculas são os "mesmos" dependentes do objeto.)  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)