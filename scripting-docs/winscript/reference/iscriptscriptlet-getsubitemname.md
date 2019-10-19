---
title: 'IScriptScriptlet:: GetSubItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b36f6dd98534b8122a6814f1fd154eca7882251a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571924"
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Retorna o último identificador no nome totalmente qualificado do host de objeto de um Scriptlet.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstr`  
 fora Se o nome do scriptlet totalmente qualificado do host tiver mais de um nível, `pbstr` retornará o endereço do buffer do identificador no segundo nível.  
  
 Se o nome do scriptlet totalmente qualificado do host tiver um nível, `pbstr` retornará o endereço do buffer do identificador no primeiro nível.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptScriptlet Interface](../../winscript/reference/iscriptscriptlet-interface.md)