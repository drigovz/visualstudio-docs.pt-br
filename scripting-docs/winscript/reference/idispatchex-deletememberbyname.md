---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 1866b5135d2c98ccacb34c2c776c69dd7d25db3f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096428"
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