---
title: 'IEnumDebugExtendedPropertyInfo:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23ebc3e3fd1f7802f4630be42a594d73f8657e43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574268"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
Recupera um número especificado de estruturas de `ExtendedDebugPropertyInfo` em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de `ExtendedDebugPropertyInfo`structures a serem recuperadas.  
  
 `rgelt`  
 fora Uma matriz de estruturas de `ExtendedDebugPropertyInfo` recuperadas.  
  
 `pceltFetched`  
 fora O número de estruturas de `ExtendedDebugPropertyInfo` realmente recuperadas.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IEnumDebugExtendedPropertyInfo](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)  
 [Estrutura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)