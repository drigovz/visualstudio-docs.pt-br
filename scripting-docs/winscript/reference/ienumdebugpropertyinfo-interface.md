---
title: Interface IEnumDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumDebugPropertyInfo interface
ms.assetid: c5eea4da-8414-408a-a8f6-6a9ca8745868
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce4f5a114629a473df99b583c77ae7747bcd339
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574182"
---
# <a name="ienumdebugpropertyinfo-interface"></a>Interface IEnumDebugPropertyInfo
Enumera estruturas de `DebugPropertyInfo`.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugPropertyInfo`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Recupera um número especificado de estruturas de `DebugPropertyInfo` em uma sequência de enumeração.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Ignora um número especificado de estruturas de `DebugPropertyInfo` em uma sequência de enumeração.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Redefine a sequência de enumeração para o início.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Obtém o número de estruturas de `DebugPropertyInfo` em um enumerador.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dbgprop. h  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)