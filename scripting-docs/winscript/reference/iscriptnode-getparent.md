---
title: 'IScriptNode:: GetParent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 58ef5f88f4404d57a7edad3590fba1d2614faec6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572563"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Retorna o objeto `IScriptNode` que é o pai de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppsnParent`  
 fora O endereço de uma variável que recebe um ponteiro para a interface de `IScriptNode` da instância pai.  
  
 Se a classe implementar `IScriptEntry` ou `IScriptScriptlet`, um objeto `IScriptNode` será retornado.  
  
 Se a classe implementa `IScriptNode` (representando uma página da Web), NULL é retornado.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)