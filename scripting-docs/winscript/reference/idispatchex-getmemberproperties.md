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
ms.openlocfilehash: 8016eef7b6e0da9b9fc88695db845cba7f608ff3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574092"
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
  
#### <a name="parameters"></a>Parâmetros  
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
  
|||  
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
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)  
 [IDispatchEx:: getdispid](../../winscript/reference/idispatchex-getdispid.md)    
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)