---
title: 'IDispatchEx:: GetMemberProperties | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 488f8790ec25532fb611f18e8b24e7e7dba2e2f4
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144540"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Recupera as propriedades de um membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>parâmetros  
 `id`  
 Identifica o membro. Usa `GetDispID` ou `GetNextDispID` para obter o identificador de expedição.  
  
 `grfdexFetch`  
 Determina quais propriedades recuperar. Isso pode ser uma combinação dos valores listados em `pgrfdex` e/ou uma combinação dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|grfdexPropCanAll|Combina fdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, fdexPropCanConstruct e fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina fdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, fdexPropCannotConstruct e fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|Combina fdexPropNoSideEffects e fdexPropDynamicType.|  
|grfdexPropAll|Combina grfdexPropCanAll, grfdexPropCannotAll e grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Endereço de um `DWORD` que recebe as propriedades solicitadas. Isso pode ser uma combinação dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexPropCanGet|O membro pode ser obtido usando DISPATCH_PROPERTYGET.|  
|fdexPropCannotGet|Não é possível obter o membro usando DISPATCH_PROPERTYGET.|  
|fdexPropCanPut|O membro pode ser definido usando DISPATCH_PROPERTYPUT.|  
|fdexPropCannotPut|O membro não pode ser definido usando DISPATCH_PROPERTYPUT.|  
|fdexPropCanPutRef|O membro pode ser definido usando DISPATCH_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|O membro não pode ser definido usando DISPATCH_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|O membro não tem nenhum efeito colateral. Por exemplo, um depurador pode obter/definir/chamar esse membro com segurança sem alterar o estado do script que está sendo depurado.|  
|fdexPropDynamicType|O membro é dinâmico e pode ser alterado durante o tempo de vida do objeto.|  
|fdexPropCanCall|O membro pode ser chamado como um método usando DISPATCH_METHOD.|  
|fdexPropCannotCall|O membro não pode ser chamado como um método usando DISPATCH_METHOD.|  
|fdexPropCanConstruct|O membro pode ser chamado como um construtor usando DISPATCH_CONSTRUCT.|  
|fdexPropCannotConstruct|O membro não pode ser chamado como um construtor usando DISPATCH_CONSTRUCT.|  
|fdexPropCanSourceEvents|O membro pode acionar eventos.|  
|fdexPropCannotSourceEvents|O membro não pode acionar eventos.|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor|Significado|
|-|-|  
|`S_OK`|Êxito.|  
|`DISP_E_UNKNOWNNAME`|O nome não era conhecido.|  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Confira também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: getdispid](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)