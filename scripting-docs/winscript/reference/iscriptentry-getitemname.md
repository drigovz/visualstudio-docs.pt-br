---
title: 'IScriptEntry:: getItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575460"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Retorna o nome do item que identifica um objeto de `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstr`  
 fora O endereço de um buffer que contém o nome do item. O nome do item é usado pelo host para identificar a entrada.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Para `IScriptScriptlet` objetos, defina o nome do item usando [IActiveScriptAuthor:: AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md). Para outras interfaces, você define o nome do item usando [IScriptEntry:: Setitemname](../../winscript/reference/iscriptentry-setitemname.md).  
  
## <a name="see-also"></a>Consulte também  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)