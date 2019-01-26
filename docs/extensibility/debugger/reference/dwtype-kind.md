---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 112250478afd142b76b1765b8f9545ac557ef13f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992250"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
Especifica como interpretar o tipo de um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 TYPE_KIND_METADATA  
 O [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) união deve ser interpretada como um [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) estrutura.  
  
 TYPE_KIND_PDB  
 O `TYPE_INFO` união deve ser interpretada como um [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) estrutura.  
  
 TYPE_KIND_BUILT  
 O `TYPE_INFO` união deve ser interpretada como um [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) estrutura.  
  
## <a name="remarks"></a>Comentários  
 Os valores dessa enumeração aparecem na `dwKind` campo do [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estruturar e são usados para determinar como interpretar o `type` membro de união. O `TYPE_INFO` estrutura é retornada por uma chamada para o [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)