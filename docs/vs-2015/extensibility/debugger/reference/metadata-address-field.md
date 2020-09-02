---
title: METADATA_ADDRESS_FIELD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3f3697473a20a2f62f4209a0bdbae89c30b8e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181150"
---
# <a name="metadata_address_field"></a>METADATA_ADDRESS_FIELD
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa estrutura representa o endereço de um campo de uma classe ou estrutura.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```csharp  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## <a name="terms"></a>Termos  
 tokField  
 A ID do token do campo.  
  
 [C++] `_mdToken` é um `typedef` para um de 32 bits `int` .  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura faz parte da União na estrutura de [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando o `dwKind` campo da `DEBUG_ADDRESS_UNION` estrutura é definido como `ADDRESS_KIND_FIELD` (um valor da enumeração [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
