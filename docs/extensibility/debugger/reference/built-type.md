---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6bf5f96d007526cecc8f2ea6b495415916ee9e4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930505"
---
# <a name="builttype"></a>BUILT_TYPE
Essa estrutura Especifica informações sobre um tipo de campo tirado de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ulAppDomainID  
 ID do aplicativo do qual o símbolo foi originada. Isso é usado para identificar exclusivamente uma instância do aplicativo.  
  
 guidModule  
 O GUID do módulo que contém esse campo.  
  
 pUnderlyingField  
 Uma [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto identifica o campo subjacente associado com esse campo interno.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é exibido como parte da união na [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estrutura quando o `dwKind` campo dos `TYPE_INFO` estrutura é definida como `TYPE_KIND_BUILT` (um valor da [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração).  
  
## <a name="requirements"></a>Requisitos  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)