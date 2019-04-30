---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000893"
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
 Determina se o nome do membro diferencia maiusculas de minúsculas. Isso pode ser um dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicitações que a pesquisa de nomes ser feita de maneira diferencia maiusculas de minúsculas. Pode ser ignorado por objeto que não oferece suporte a pesquisa diferencia maiusculas de minúsculas.|  
|fdexNameCaseInsensitive|Solicitações que a pesquisa de nomes ser feita em diferenciando maiusculas de minúsculas. Pode ser ignorado por objeto que não oferece suporte a pesquisa diferencia maiusculas de minúsculas.|  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|||  
|-|-|  
|`S_OK`|Êxito.|  
|`S_FALSE`|Membro existe, mas não pode ser excluído.|  
  
## <a name="remarks"></a>Comentários  
 Se o membro for excluído, o DISPID deve permanecer válida para `GetNextDispID`.  
  
 Se um membro com um determinado nome é excluído e posteriormente um membro com o mesmo nome é recriado, o DISPID deve ser o mesmo. (Se os membros que diferem somente maiusculas são "mesmo" é o objeto dependente).  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)