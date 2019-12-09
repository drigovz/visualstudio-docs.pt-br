---
title: 'IDebugApplicationNode:: fechar | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Close
ms.assetid: ea8db480-2344-4c7b-960c-4fa97fa6c1b7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 928dc94a5d700b2cad6a7acfb59a409240be7dc3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574835"
---
# <a name="idebugapplicationnodeclose"></a>IDebugApplicationNode::Close
Faz com que este aplicativo libere todas as referências e insira um estado inativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, o proprietário de um aplicativo chama esse método quando o aplicativo é encerrado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)