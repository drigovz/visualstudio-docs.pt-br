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
ms.openlocfilehash: 736bea847908e3c70d6caf2f8e41af38608f4f23
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963423"
---
# <a name="ienumdebugpropertyinfo-interface"></a>Interface IEnumDebugPropertyInfo
Enumera `DebugPropertyInfo` estruturas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugPropertyInfo`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IEnumDebugPropertyInfo::Next](../../winscript/reference/ienumdebugpropertyinfo-next.md)|Recupera um número especificado de `DebugPropertyInfo` estruturas em uma sequência de enumeração.|  
|[IEnumDebugPropertyInfo::Skip](../../winscript/reference/ienumdebugpropertyinfo-skip.md)|Ignora um número especificado de `DebugPropertyInfo` estruturas em uma sequência de enumeração.|  
|[IEnumDebugPropertyInfo::Reset](../../winscript/reference/ienumdebugpropertyinfo-reset.md)|Redefine a sequência de enumeração para o início.|  
|[IEnumDebugPropertyInfo::Clone](../../winscript/reference/ienumdebugpropertyinfo-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[IEnumDebugPropertyInfo::GetCount](../../winscript/reference/ienumdebugpropertyinfo-getcount.md)|Obtém o número de `DebugPropertyInfo` estruturas em um enumerador.|  
  
## <a name="requirements"></a>Requisitos  
 Header: dbgprop.h  
  
## <a name="see-also"></a>Consulte também  
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)