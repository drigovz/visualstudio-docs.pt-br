---
title: IDebugApplicationNode::D Etach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Detach
ms.assetid: 36bb3e54-a4df-48d5-a6de-3b8d4c0e98a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ffb422bec21bec65f1550368d898608a5f65015
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574804"
---
# <a name="idebugapplicationnodedetach"></a>IDebugApplicationNode::Detach
Remove este nó de aplicativo da árvore do projeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método remove este nó de aplicativo da árvore do projeto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode:: anexar](../../winscript/reference/idebugapplicationnode-attach.md)    
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)