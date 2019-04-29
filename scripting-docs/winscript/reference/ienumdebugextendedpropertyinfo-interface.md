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
ms.openlocfilehash: 2440daf99d9dbb69713d1895ffbfaa18965480a4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963462"
---
# <a name="ienumdebugextendedpropertyinfo-interface"></a>Interface IEnumDebugExtendedPropertyInfo
Enumera `ExtendedDebugPropertyInfo` estruturas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugExtendedPropertyInfo`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IEnumDebugExtendedPropertyInfo::Clone](../../winscript/reference/ienumdebugextendedpropertyinfo-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[IEnumDebugExtendedPropertyInfo::GetCount](../../winscript/reference/ienumdebugextendedpropertyinfo-getcount.md)|Obtém o número de `ExtendedDebugPropertyInfo` estruturas em um enumerador.|  
|[IEnumDebugExtendedPropertyInfo::Next](../../winscript/reference/ienumdebugextendedpropertyinfo-next.md)|Recupera um número especificado de `ExtendedDebugPropertyInfo` estruturas em uma sequência de enumeração.|  
|[IEnumDebugExtendedPropertyInfo::Skip](../../winscript/reference/ienumdebugextendedpropertyinfo-skip.md)|Ignora um número especificado de `ExtendedDebugPropertyInfo` estruturas em uma sequência de enumeração.|  
|[IEnumDebugExtendedPropertyInfo::Reset](../../winscript/reference/ienumdebugextendedpropertyinfo-reset.md)|Redefine a sequência de enumeração para o início.|  
  
## <a name="requirements"></a>Requisitos  
 Header: dbgprop.h  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)