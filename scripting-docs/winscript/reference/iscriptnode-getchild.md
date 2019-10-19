---
title: 'IScriptNode:: GetChild | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573560"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Retorna o filho que está no índice especificado no nó.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `isn`  
 no O índice do filho no pai.  
  
 `ppsn`  
 fora O endereço de uma variável que recebe um ponteiro para a interface de `IScriptNode` da instância filho.  
  
 Para `IScriptNode` objetos que representam uma página da Web, esse parâmetro retorna um objeto que contém um bloco de script.  
  
 Para `IScriptEntry` objetos que especificam um bloco de script, esse parâmetro retorna um objeto que especifica uma função.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Para `IScriptEntry` objetos que especificam um objeto de função e para `IScriptScriptlet` objetos, esse método falha porque não há entradas filhas.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)