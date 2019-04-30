---
title: IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f909a63f0f7ba70fca3c5e30e32a2d64c0147e9c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979169"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Retorna uma interface de eventos que encapsula um determinado `IDispatch` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdisp`  
 [in] O `IDispatch` objeto a ser encapsulado.  
  
 `ppscp`  
 [out] A interface de eventos que encapsula `pdisp`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Retorna uma interface de eventos que encapsula o determinado `IDispatch` (consulte [ISimpleConnectionPoint Interface](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)