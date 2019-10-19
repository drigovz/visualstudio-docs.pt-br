---
title: 'IEnumDebugPropertyInfo:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::Skip
ms.assetid: 2f6361fb-d66d-4fc0-8fe0-c859593a183f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba634409fb051c37534c824efb20e33eda245e8a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574164"
---
# <a name="ienumdebugpropertyinfoskip"></a>IEnumDebugPropertyInfo::Skip
Ignora um número especificado de estruturas de `DebugPropertyInfo` em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Skip(  
   ULONGcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de estruturas de `DebugPropertyInfo` na sequência de enumeração a serem ignoradas.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`. Retorna `S_FALSE` e define o ponteiro do elemento atual como o final da enumeração se `celt` for maior que o número de elementos restantes no enumerador.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)