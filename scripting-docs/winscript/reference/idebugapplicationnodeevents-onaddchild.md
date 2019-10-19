---
title: 'IDebugApplicationNodeEvents:: onAddChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAddChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 052fe47f1ddf2d20e7486a95a9dd79bc388f7ebc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574702"
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Manipula o evento quando um nó filho é adicionado a um objeto de nó de aplicativo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `prddpChild`  
 no O nó de aplicativo de depuração filho que foi adicionado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método trata o evento quando um nó filho é adicionado a um objeto de nó de aplicativo de depuração.  
  
 Implementadores da interface `IDebugApplicationNode` acionam este evento  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents:: onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)    
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)