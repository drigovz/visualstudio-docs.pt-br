---
title: 'IDebugApplicationNodeEvents:: onRemoveChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0ff7b28f14c26029d64197ba919cc97c90a856c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574665"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Manipula o evento quando um nó filho é removido de um objeto de nó de aplicativo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `prddpChild`  
 no O nó do aplicativo filho que foi removido.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método trata o evento quando um nó filho é removido de um objeto de nó de aplicativo de depuração.  
  
 Os implementadores da interface `IDebugApplicationNode` geram esse evento.  
  
## <a name="see-also"></a>Consulte também  
   de [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)