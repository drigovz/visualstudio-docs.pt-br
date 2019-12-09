---
title: 'IScriptScriptlet:: SetSubItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab4f7afec9302126ccbfcbe7f2abafc74cbf17d6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571852"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Define o último identificador no nome totalmente qualificado do host de objeto de um Scriptlet.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `psz`  
 Se o nome do scriptlet totalmente qualificado do host tiver mais de um nível, `psz` será o endereço do buffer do identificador no segundo nível.  
  
 Se o nome do scriptlet totalmente qualificado do host tiver um nível, `psz` será o endereço do buffer do identificador no primeiro nível.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptScriptlet Interface](../../winscript/reference/iscriptscriptlet-interface.md)