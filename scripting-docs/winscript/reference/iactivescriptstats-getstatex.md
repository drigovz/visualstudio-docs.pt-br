---
title: 'IActiveScriptStats:: GetStatEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576117"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Retorna uma estatística de script personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guid`  
 no Especifica qual estatística retornar. A semântica da estatística que corresponde a um GUID específico é totalmente definida pelo mecanismo.  
  
 `pluHi`  
 fora Os bits de 32 altos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
 `pluLo`  
 fora Os bits de 32 baixos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que um mecanismo de script personalizado retorne estatísticas significativas para um host personalizado.  
  
> [!NOTE]
> Este método não está implementado no momento.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptStats:: getstat](../../winscript/reference/iactivescriptstats-getstat.md)    
 [IActiveScriptStats Interface](../../winscript/reference/iactivescriptstats-interface.md)