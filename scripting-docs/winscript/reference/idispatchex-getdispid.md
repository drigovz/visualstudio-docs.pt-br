---
title: 'IDispatchEx:: getdispid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144527"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapeia um único nome de membro para seu DISPID correspondente, que pode ser usado em chamadas subsequentes para `IDispatchEx::InvokeEx` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>parâmetros  
 `bstrName`  
 Passado no nome a ser mapeado.  
  
 `grfdex`  
 Determina as opções para obter o identificador de membro. Isso pode ser uma combinação dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicita que a pesquisa de nome seja feita de maneira diferenciada de maiúsculas e minúsculas. Pode ser ignorado por um objeto que não dá suporte à pesquisa que diferencia maiúsculas de minúsculas.|  
|fdexNameEnsure|Solicita que o membro seja criado se ele ainda não existir. O novo membro deve ser criado com o valor `VT_EMPTY` .|  
|fdexNameImplicit|Indica que o chamador está pesquisando objeto (s) para um membro de um nome específico quando o objeto base não é especificado explicitamente.|  
|fdexNameCaseInsensitive|Solicita que a pesquisa de nome seja feita de maneira não diferencia maiúsculas de minúsculas. Pode ser ignorado por um objeto que não dá suporte à pesquisa que não diferencia maiúsculas de minúsculas.|  
  
 `pid`  
 Ponteiro para local alocado pelo chamador para receber o resultado DISPID. Se ocorrer um erro, `pid` conterá DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor|Significado|
|-|-|  
|`S_OK`|Êxito.|  
|`E_OUTOFMEMORY`|Memória insuficiente.|  
|`DISP_E_UNKNOWNNAME`|O nome não era conhecido.|  
  
## <a name="remarks"></a>Comentários  
 `GetDispID` pode ser usado em vez de `GetIDsOfNames` obter o DISPID para um determinado membro.  
  
 Como `IDispatchEx` permite a adição e a exclusão de membros, o conjunto de DISPIDs não permanece constante durante o tempo de vida de um objeto.  
  
 O parâmetro não usado `riid` no `IDispatch::GetIDsOfNames` foi removido.  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Confira também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)