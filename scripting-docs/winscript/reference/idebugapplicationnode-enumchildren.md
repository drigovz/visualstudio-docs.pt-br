---
title: IDebugApplicationNode::EnumChildren | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.EnumChildren
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::EnumChildren
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4967f35904a32e9b9a82426273ea7fd651a34b5a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088121"
---
# <a name="idebugapplicationnodeenumchildren"></a>IDebugApplicationNode::EnumChildren
Enumera os nós filho deste nó de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pperddp`  
 [out] A enumeração de nós de filhos deste nó.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método enumera os nós filho deste nó de aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)