---
title: IActiveScriptAuthor::GetEventHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086678"
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
 [in] O `IDispatch` objeto que corresponde ao `NamedItem` à qual o scriptlet está associado.  
  
 `pszItem`  
 [in] O endereço do buffer do identificador de nível superior do nome totalmente qualificado de scriptlet no host.  
  
 `pszSubItem`  
 [in] O endereço do buffer do identificador do nome totalmente qualificado de scriptlet no host do segundo nível. Definido como NULL se o nome tem apenas um nível.  
  
 `pszEvent`  
 [in] O endereço de um buffer que contém o nome do evento. O scriptlet é um manipulador de eventos para este evento.  
  
 `ppse`  
 [out] O endereço de uma variável que recebe um ponteiro para o `IScriptEntry` interface do scriptlet que tem os atributos especificados.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)