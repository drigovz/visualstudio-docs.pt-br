---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086587"
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