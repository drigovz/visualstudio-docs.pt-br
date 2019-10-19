---
title: 'IActiveScriptAuthor:: geteventhandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576223"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Retorna o scriptlet que tem os atributos especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdisp`  
 no O objeto `IDispatch` que corresponde ao `NamedItem` ao qual o scriptlet está anexado.  
  
 `pszItem`  
 no O endereço de buffer do identificador de nível superior do nome do scriptlet totalmente qualificado no host.  
  
 `pszSubItem`  
 no O endereço de buffer do identificador de segundo nível do nome totalmente qualificado do scriptlet no host. Defina como NULL se o nome tiver apenas um nível.  
  
 `pszEvent`  
 no O endereço de um buffer que contém o nome do evento. O scriptlet é um manipulador de eventos para esse evento.  
  
 `ppse`  
 fora O endereço de uma variável que recebe um ponteiro para a interface `IScriptEntry` do scriptlet que tem os atributos especificados.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)