---
title: 'IScriptEntry:: GetRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6e1b1600c93aa05bbe9669fb57a23a8c9344a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575433"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Retorna a posição inicial e o comprimento de uma entrada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pichMin`  
 fora Para `IScriptEntry` objetos que especificam um bloco de script, retorna 0.  
  
 Para `IScriptEntry` objetos que especificam um objeto de função, retorna a posição inicial da função no bloco de script atual.  
  
 Para objetos `IScriptScriptlet`, retorna 0.  
  
 `pcch`  
 fora Para `IScriptEntry` objetos que especificam um bloco de script, retorna o comprimento do texto.  
  
 Para `IScriptEntry` objetos que especificam um objeto de função, retorna o comprimento da definição da função.  
  
 Para objetos `IScriptScriptlet`, retorna o comprimento da entrada.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)