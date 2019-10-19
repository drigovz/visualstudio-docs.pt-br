---
title: 'IScriptNode:: Alive | Microsoft Docs'
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
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573625"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indica se um objeto ainda está ativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O nó de script ainda está ativo.|  
  
## <a name="remarks"></a>Comentários  
 Se o objeto não estiver ativo, Component Object Model (COM) retornará um erro do proxy de marshaling para chamadas para esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)