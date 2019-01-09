---
title: 'Iactivescriptsite:: getItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f4dc6515d64406870ca10f003d7cea515c49b7d8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095882"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Permite que o mecanismo de script obter informações sobre um item adicionado com o [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.  
  
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
 [in] O nome associado ao item, conforme especificado na [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.  
  
 `dwReturnMask`  
 [in] Uma máscara de bits que especifica quais informações sobre o item devem ser retornadas. O mecanismo de script deve solicitar a quantidade mínima de informações possíveis porque alguns dos parâmetros de retorno (por exemplo, `ITypeInfo`) pode levar um tempo considerável para carregar ou gerar. Pode ser uma combinação dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Retorna o `IUnknown` interface para este item.|  
|SCRIPTINFO_ITYPEINFO|Retorna o `ITypeInfo` interface para este item.|  
  
 `ppunkItem`  
 [out] Endereço de uma variável que recebe um ponteiro para o `IUnknown` interface associada com o item determinado. O mecanismo de script pode usar o `IUnknown::QueryInterface` método para obter o `IDispatch` interface para o item. Esse parâmetro recebe um valor nulo se `dwReturnMask` não inclui o valor SCRIPTINFO_IUNKNOWN. Além disso, ele recebe um valor nulo se não houver nenhum objeto associado com o nome do item; Esse mecanismo é usado para criar uma classe simples, quando o item nomeado foi adicionado com o sinalizador SCRIPTITEM_CODEONLY definido [Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) método.  
  
 `ppTypeInfo`  
 [out] Endereço de uma variável que recebe um ponteiro para o `ITypeInfo` interface associado ao item. Esse parâmetro recebe um valor nulo se `dwReturnMask` não inclui o valor SCRIPTINFO_ITYPEINFO, ou se as informações de tipo não estão disponíveis para este item. Se as informações de tipo não estão disponíveis, o objeto não é possível obter eventos e associação de nome precisa ser realizada com o `IDispatch::GetIDsOfNames` método. Observe que o `ITypeInfo` interface recuperado descreve coclass do item (TKIND_COCLASS) porque o objeto pode dar suporte a várias interfaces e interfaces de evento. Se o item oferece suporte a `IProvideMultipleTypeInfo` interface, o `ITypeInfo` interface recuperado é o mesmo que o índice zero `ITypeInfo` que seria obtido usando o `IProvideMultipleTypeInfo::GetInfoOfIndex` método.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`TYPE_E_ELEMENTNOTFOUND`|Um item do nome especificado não foi encontrado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera apenas as informações indicadas pelo `dwReturnMask` parâmetro; Isso melhora o desempenho. Por exemplo, se um `ITypeInfo` interface não é necessária para um item, ele simplesmente não é especificado em `dwReturnMask`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)