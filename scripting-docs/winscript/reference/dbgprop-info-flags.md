---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572584"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Usado para especificar campos de `DebugPropertyInfo`  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Membros  
 DBGPROP_INFO_NAME  
 Inicializa o campo `bstrName`.  
  
 DBGPROP_INFO_TYPE  
 Inicializa o campo `bstrType`.  
  
 DBGPROP_INFO_VALUE  
 Inicializa o campo `bstrValue`.  
  
 DBGPROP_INFO_FULLNAME  
 Inicializa o campo `bstrFullName`.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Inicializa o campo `dwAttrib`.  
  
 DBGPROP_INFO_DEBUGPROP  
 Inicializa o campo `pDebugProp` que contém uma interface `IDebugProperty`.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Especifica que o campo de valor deve conter o valor expandido automaticamente, se disponível, para esse tipo de objeto.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 [estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)