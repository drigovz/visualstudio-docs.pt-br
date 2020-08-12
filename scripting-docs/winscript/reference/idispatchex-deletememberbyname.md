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
ms.openlocfilehash: cf62972b192d73bd130d15066d79ea70fe24beb8
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144591"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Exclui um membro por nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>parâmetros  
 `bstrName`  
 Nome do membro a ser excluído.  
  
 `grfdex`  
 Determina se o nome do membro diferencia maiúsculas de minúsculas. Esse valor pode ser um dos seguintes:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicita que a pesquisa de nome seja feita de maneira diferenciada de maiúsculas e minúsculas. Pode ser ignorado por um objeto que não dá suporte à pesquisa que diferencia maiúsculas de minúsculas.|  
|fdexNameCaseInsensitive|Solicita que a pesquisa de nome seja feita de maneira não diferencia maiúsculas de minúsculas. Pode ser ignorado por um objeto que não dá suporte à pesquisa que não diferencia maiúsculas de minúsculas.|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor|Significado|
|-|-|  
|`S_OK`|Êxito.|  
|`S_FALSE`|O membro existe, mas não pode ser excluído.|  
  
## <a name="remarks"></a>Comentários  
 Se o membro for excluído, o DISPID precisa permanecer válido para `GetNextDispID` .  
  
 Se um membro com um determinado nome for excluído e posteriormente um membro com o mesmo nome for recriado, o DISPID deverá ser o mesmo. (Se os membros que diferem apenas em maiúsculas e minúsculas são os "mesmos" dependentes do objeto.)  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Confira também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)