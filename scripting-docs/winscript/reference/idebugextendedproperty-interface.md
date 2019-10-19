---
title: Interface IDebugExtendedProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedProperty interface
ms.assetid: e92ea064-0d92-44cf-bb9f-abda783d84be
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24a93cb3bd230e2489b58d78f6d414ba1df006ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572498"
---
# <a name="idebugextendedproperty-interface"></a>Interface IDebugExtendedProperty
Estende a interface `IDebugProperty`.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 Além dos métodos herdados de `IDebugProperty`, essa interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugExtendedProperty::GetExtendedPropertyInfo](../../winscript/reference/idebugextendedproperty-getextendedpropertyinfo.md)|Obtém o `ExtendedDebugPropertyInfo` que descreve este `IDebugExtendedProperty``.`|  
|[IDebugExtendedProperty::EnumExtendedMembers](../../winscript/reference/idebugextendedproperty-enumextendedmembers.md)|Enumera os membros de uma propriedade estendida.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dbgprop. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)