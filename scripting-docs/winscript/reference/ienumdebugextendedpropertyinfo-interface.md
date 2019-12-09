---
title: Interface IEnumDebugExtendedPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo interface
ms.assetid: 316d5aa7-c949-48fc-89c1-239f00566cae
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ceae13f2a785a0920598fa79b237a9c8ae1da1c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568935"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>Interface IEnumDebugExtendedPropertyInfo
Enumera estruturas de `ExtendedDebugPropertyInfo`.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugExtendedPropertyInfo`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Obtém o número de estruturas de `ExtendedDebugPropertyInfo` em um enumerador.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Recupera um número especificado de estruturas de `ExtendedDebugPropertyInfo` em uma sequência de enumeração.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Ignora um número especificado de estruturas de `ExtendedDebugPropertyInfo` em uma sequência de enumeração.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Redefine a sequência de enumeração para o início.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dbgprop. h  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)