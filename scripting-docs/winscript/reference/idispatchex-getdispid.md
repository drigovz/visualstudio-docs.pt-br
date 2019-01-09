---
title: IDispatchEx::GetDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c466ec767be53d100b970314bf0d81d5dd9dfb20
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097533"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Mapeia um nome de membro único para seu DISPID correspondente, que pode ser usado em chamadas subsequentes para `IDispatchEx::InvokeEx`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bstrName`  
 Passado nome a ser mapeada.  
  
 `grfdex`  
 Determina as opções para obter o identificador de membro. Isso pode ser uma combinação dos seguintes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|fdexNameCaseSensitive|Solicitações que a pesquisa de nomes ser feita de maneira diferencia maiusculas de minúsculas. Pode ser ignorado por objeto que não oferece suporte a pesquisa diferencia maiusculas de minúsculas.|  
|fdexNameEnsure|Solicita que o membro criado se ele ainda não existir. O novo membro deve ser criado com o valor `VT_EMPTY`.|  
|fdexNameImplicit|Indica que o chamador está pesquisando (s) de um membro de um nome específico quando o objeto base não for especificado explicitamente.|  
|fdexNameCaseInsensitive|Solicitações que a pesquisa de nomes ser feita em diferenciando maiusculas de minúsculas. Pode ser ignorado por objeto que não oferece suporte a pesquisa diferencia maiusculas de minúsculas.|  
  
 `pid`  
 Ponteiro para o local alocada pelo chamador para receber DISPID resultado. Se ocorrer um erro, `pid` contém DISPID_UNKNOWN.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|||  
|-|-|  
|`S_OK`|Êxito.|  
|`E_OUTOFMEMORY`|Memória insuficiente.|  
|`DISP_E_UNKNOWNNAME`|O nome não era conhecido.|  
  
## <a name="remarks"></a>Comentários  
 `GetDispID` pode ser usado em vez de `GetIDsOfNames` para obter o DISPID para um determinado membro.  
  
 Porque `IDispatchEx` permite a adição e exclusão de membros, o conjunto de DISPIDs não permanecem constantes durante a vida útil de um objeto.  
  
 O não utilizado `riid` parâmetro no `IDispatch::GetIDsOfNames` foi removido.  
  
## <a name="example"></a>Exemplo  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)