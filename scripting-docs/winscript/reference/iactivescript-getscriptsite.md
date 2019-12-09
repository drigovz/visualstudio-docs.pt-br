---
title: 'IActiveScript:: GetScriptSite | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575739"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Recupera o objeto do site associado ao mecanismo de script do Windows.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iid`  
 no Identificador da interface solicitada.  
  
 `ppvSiteObject`  
 fora Endereço do local que recebe o ponteiro de interface para o objeto do site do host.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_NOINTERFACE`|Não há suporte para a interface especificada.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`S_FALSE`|Nenhum site foi definido; o parâmetro `ppvSiteObject` é definido como `NULL`.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)