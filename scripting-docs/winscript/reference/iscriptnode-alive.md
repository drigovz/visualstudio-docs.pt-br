---
title: IScriptNode::Alive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 23f0e804cbbbe6683b89f7b629b9677c7b92c64f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089551"
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