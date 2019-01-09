---
title: IScriptNode::GetIndexInParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c484d212e2dccf20717aec5dca44d5c3319e15c9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089564"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Retorna o índice de um objeto na lista de filhos do pai.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pisn`  
 [out] Retorna o índice de um objeto na lista de filhos do pai.  
  
 Se esse método for chamado por um `IScriptNode` do objeto que representa uma página da Web, esse parâmetro retorna 0.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)