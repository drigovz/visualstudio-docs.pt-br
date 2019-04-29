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
ms.openlocfilehash: 27aaadfd1d3ff38e9a0382ff1863b73d2bccc325
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539437"
---
# <a name="jspropertyattributes-enumeration"></a>Enumeração JS_PROPERTY_ATTRIBUTES
Indica os atributos de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Membros  
  
|Nome|Descrição|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|A propriedade não tem atributos.|  
|`JS_PROPERTY_HAS_CHILDREN`|A propriedade tem filhos.|  
|`JS_PROPERTY_FAKE`|A propriedade representa um nó falso, como "[métodos]".|  
|`JS_PROPERTY_METHOD`|A propriedade é um método.|  
|`JS_PROPERTY_READONLY`|A propriedade é somente leitura.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|A propriedade é um ponteiro para um objeto nativo do WinRT.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)