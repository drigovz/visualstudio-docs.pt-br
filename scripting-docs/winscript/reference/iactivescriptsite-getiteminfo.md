---
title: 'IActiveScriptSite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570921"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Permite que o mecanismo de script Obtenha informações sobre um item adicionado com o método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrName`  
 no O nome associado ao item, conforme especificado no método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 no Uma máscara de bits que especifica quais informações sobre o item devem ser retornadas. O mecanismo de script deve solicitar a quantidade mínima de informações possíveis porque alguns dos parâmetros de retorno (por exemplo, `ITypeInfo`) podem levar um tempo considerável para carregar ou gerar. Pode ser uma combinação dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Retorna a interface `IUnknown` para este item.|  
|SCRIPTINFO_ITYPEINFO|Retorna a interface `ITypeInfo` para este item.|  
  
 `ppunkItem`  
 fora Endereço de uma variável que recebe um ponteiro para a interface de `IUnknown` associada ao item especificado. O mecanismo de script pode usar o método `IUnknown::QueryInterface` para obter a interface `IDispatch` para o item. Esse parâmetro receberá NULL se `dwReturnMask` não incluir o valor SCRIPTINFO_IUNKNOWN. Além disso, ele receberá NULL se não houver nenhum objeto associado ao nome do item; Esse mecanismo é usado para criar uma classe simples quando o item nomeado foi adicionado com o sinalizador SCRIPTITEM_CODEONLY definido no método [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 fora Endereço de uma variável que recebe um ponteiro para a interface `ITypeInfo` associada ao item. Esse parâmetro receberá NULL se `dwReturnMask` não incluir o valor SCRIPTINFO_ITYPEINFO ou se as informações de tipo não estiverem disponíveis para este item. Se as informações de tipo não estiverem disponíveis, o objeto não poderá eventos de origem e a associação de nome deverá ser realizada com o método `IDispatch::GetIDsOfNames`. Observe que a interface `ITypeInfo` recuperada descreve a coclasse do item (TKIND_COCLASS) porque o objeto pode dar suporte a várias interfaces e interfaces de evento. Se o item der suporte à interface `IProvideMultipleTypeInfo`, a interface `ITypeInfo` recuperada será a mesma que a `ITypeInfo` de índice zero que seria obtida usando o método `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`TYPE_E_ELEMENTNOTFOUND`|Um item do nome especificado não foi encontrado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera apenas as informações indicadas pelo parâmetro `dwReturnMask`; Isso melhora o desempenho. Por exemplo, se uma interface de `ITypeInfo` não for necessária para um item, ela simplesmente não será especificada em `dwReturnMask`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)