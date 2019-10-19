---
title: 'ICanHandleException:: canmanipuleexception | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575715"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
Determina se o chamador do mecanismo de script pode manipular uma exceção especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pExcepInfo`  
 no Ponteiro para uma estrutura de `EXCEPINFO` que contém as informações que serão relatadas se nenhum manipulador de exceção for encontrado.  
  
 `pvar`  
 no Um valor associado à exceção, como o valor lançado por uma instrução `throw`. Esse parâmetro pode ser `NULL`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O chamador pode manipular a exceção|  
|`E_FAIL`|O chamador não pode manipular a exceção.|  
  
## <a name="remarks"></a>Comentários  
 Se uma chamada para `IDispatchEx::InvokeEx`, ou um método semelhante, resultar em uma exceção, o mecanismo de script verificará se há um chamador na cadeia de chamada do script que dá suporte à interface `ICanHandleException` e indica que ela pode manipular a exceção. Se nenhum chamador puder manipular a exceção, o mecanismo de script é interrompido.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface ICanHandleException](../../winscript/reference/icanhandleexception-interface.md)  
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)