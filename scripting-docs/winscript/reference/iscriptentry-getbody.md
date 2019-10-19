---
title: 'IScriptEntry:: GetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba6019f4729f1b4a31933a4ca93c0eddf6159a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575482"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Retorna o texto que corresponde ao corpo de um bloco de script `IScriptEntry`, bloco de função ou scriptlet.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstr`  
 fora O texto que está no corpo de um dos seguintes:  
  
- Um bloco de script `IScriptEntry`  
  
- Uma função `IScriptEntry` em um bloco de função  
  
- Um manipulador de eventos `IScriptEntry` scriptlet  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)