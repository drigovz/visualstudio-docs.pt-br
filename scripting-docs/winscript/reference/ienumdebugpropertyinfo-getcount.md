---
title: 'IEnumDebugPropertyInfo:: GetCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugPropertyInfo.GetCount
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugPropertyInfo::GetCount
ms.assetid: 83a3becd-8533-4880-9c4f-193227ff25a9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fea4872761dbc67a297400dba77f660ae2e3076b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574216"
---
# <a name="ienumdebugpropertyinfogetcount"></a>IEnumDebugPropertyInfo::GetCount
Obtém o número de estruturas de `DebugPropertyInfo` no enumerador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetCount (  
   ULONG* pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcelt`  
 fora Retorna o número de estruturas de `DebugPropertyInfo` no enumerador.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)  
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)