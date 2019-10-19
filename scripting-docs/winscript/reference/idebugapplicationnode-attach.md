---
title: 'IDebugApplicationNode:: Attach | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574781"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Adiciona este nó de aplicativo à árvore de projeto especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdanParent`  
 no A árvore de projeto onde este nó de aplicativo deve ser adicionado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método adiciona este nó de aplicativo à árvore do projeto, usando `pdanParent` como o pai. Se `pdanParent` for `NULL`, esse nó de aplicativo será o nó de nível superior.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode::D etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)