---
title: 'IDebugApplicationNodeEvents:: ondetach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onDetach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onDetach
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb1a33cbec8ef032c1c4fedba28ad4013e676f0d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574673"
---
# <a name="idebugapplicationnodeeventsondetach"></a>IDebugApplicationNodeEvents::onDetach
Manipula um evento que significa que o objeto depurar nó do aplicativo foi desanexado de um nó pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onDetach();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método trata um evento que significa que o objeto depurar nó do aplicativo foi desanexado de um nó pai.  
  
 Os implementadores da interface `IDebugApplicationNode` geram esse evento.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
 [IDebugApplicationNodeEvents:: onattach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)    
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)