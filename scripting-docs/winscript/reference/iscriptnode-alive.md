---
title: IScriptNode::Alive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159212"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indica se um objeto ainda está ativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O nó de script ainda está ativo.|  
  
## <a name="remarks"></a>Comentários  
 Se o objeto não estiver ativo, o modelo de objeto de componente (COM) retornará um erro do proxy marshaling de chamadas para esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)