---
title: IScriptNode::GetChild | Microsoft Docs
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
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787124"
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
 [in] O índice do filho no pai.  
  
 `ppsn`  
 [out] O endereço de uma variável que recebe um ponteiro para o `IScriptNode` interface da instância filho.  
  
 Para `IScriptNode` objetos que representam uma página da Web, este parâmetro retorna um objeto que contém um bloco de script.  
  
 Para `IScriptEntry` objetos que especificam um bloco de script, esse parâmetro retorna um objeto que especifica uma função.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Para `IScriptEntry` objetos que especificam um objeto de função e para `IScriptScriptlet` objetos, esse método falhar porque não existem entradas filho.  
  
## <a name="see-also"></a>Consulte também  
 [IScriptNode Interface](../../winscript/reference/iscriptnode-interface.md)