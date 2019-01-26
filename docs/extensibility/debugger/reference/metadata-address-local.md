---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b29c9ec3d424dfb88f4cbe14e6e8baea87737d8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916654"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
Essa estrutura representa o endereço de uma variável local dentro de um escopo (geralmente uma função ou método).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Termos  
 tokMethod  
 A ID do método ou da função variável local é parte do.  
  
 [C++] `_mdToken` é um `typedef` de 32 bits `int`.  
  
 pLocal  
 O token cujo endereço representa essa estrutura.  
  
 dwIndex  
 Pode ser o índice dessa variável local no método ou função ou algum outro valor (específico do idioma).  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é parte da união na [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estrutura quando o `dwKind` campo dos `DEBUG_ADDRESS_UNION` estrutura é definida como `ADDRESS_KIND_LOCAL` (um valor da [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeração).  
  
 `Warning:` [C++]  Se `pLocal` não for nulo, então você deve chamar `Release` no ponteiro de token (`addr` é um campo no [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)