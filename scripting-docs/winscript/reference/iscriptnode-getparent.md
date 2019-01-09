---
title: IScriptNode::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b45fc7be1a5178e952fefcd794171410d149a1f4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090019"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Retorna o `IScriptNode` objeto que é o pai de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppsnParent`  
 [out] O endereço de uma variável que recebe um ponteiro para o `IScriptNode` interface da instância pai.  
  
 Se a classe implementa `IScriptEntry` ou `IScriptScriptlet`, um `IScriptNode` objeto é retornado.  
  
 Se a classe implementa `IScriptNode` (que representa uma página da Web), NULL será retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)