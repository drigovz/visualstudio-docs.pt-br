---
title: Enumeração JS_PROPERTY_ATTRIBUTES | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94a72228e1ad6ab49568f3291ad9add7209ef3da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571742"
---
# <a name="js_property_attributes-enumeration"></a>Enumeração JS_PROPERTY_ATTRIBUTES
Indica os atributos de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Membros  
  
|Name|Descrição|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|A propriedade não tem atributos.|  
|`JS_PROPERTY_HAS_CHILDREN`|A propriedade tem filhos.|  
|`JS_PROPERTY_FAKE`|A propriedade representa um nó falso, como "[Methods]".|  
|`JS_PROPERTY_METHOD`|A propriedade é um método.|  
|`JS_PROPERTY_READONLY`|A propriedade é somente leitura.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|A propriedade é um ponteiro para um objeto WinRT nativo.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)