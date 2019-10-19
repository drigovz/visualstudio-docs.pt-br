---
title: 'IDebugApplicationNodeEvents:: onattach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e45af6b931dad28a41f8f4453db9fab96405df3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574689"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Manipula um evento que significa que o objeto depurar nó do aplicativo foi anexado a um nó pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `prddpParent`  
 no O nó do aplicativo de depuração que é o pai deste nó.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método trata um evento que significa que o objeto depurar nó do aplicativo foi anexado a um nó pai.  
  
 Os implementadores da interface `IDebugApplicationNode` geram esse evento.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents:: desanexar](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)    
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)