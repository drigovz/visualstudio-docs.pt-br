---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12102c297c34649c753cf1c811994f9e750b9605
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838491"
---
# <a name="type_info"></a>TYPE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa estrutura especifica vários tipos de informações sobre o tipo de um campo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
struct _tagTYPE_INFO_UNION {  
   dwTYPE_KIND dwKind;  
   union {  
      METADATA_TYPE typeMeta;  
      PDB_TYPE      typePdb;  
      BUILT_TYPE    typeBuilt;  
      DWORD         unused;  
   } type;  
} TYPE_INFO;  
```  
  
```csharp  
public struct TYPE_INFO {  
   public uint   dwKind;  
   public IntPtr unionmember;  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 dwKind  
 Um valor da enumeração [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) que determina como interpretar a União.  
  
 Digite. typeMeta  
 [Somente C++] Contém uma estrutura de [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) se `dwKind` for `TYPE_KIND_METADATA` .  
  
 Digite. typePdb  
 [Somente C++] Contém uma estrutura de [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) se `dwKind` for `TYPE_KIND_PDB` .  
  
 Digite. typeBuilt  
 [Somente C++] Contém uma estrutura de [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) se `dwKind` for `TYPE_KIND_BUILT` .  
  
 tipo. não usado  
 Preenchimento não usado.  
  
 type  
 Nome da União.  
  
 unionmember  
 [Somente C#] Realize o marshaling para o tipo de estrutura apropriado com base em `dwKind` .  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o método [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) onde está preenchida. Como o conteúdo da estrutura é interpretado baseia-se no `dwKind` campo.  
  
> [!NOTE]
> [Somente C++] Se for `dwKind` igual a `TYPE_KIND_BUILT` , será necessário liberar o objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) subjacente ao destruir a `TYPE_INFO` estrutura. Isso é feito chamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.  
  
 [Somente C#] A tabela a seguir mostra como interpretar o `unionmember` membro para cada tipo de tipo. O exemplo mostra como isso é feito para um tipo de tipo.  
  
|`dwKind`|`unionmember` interpretado como|  
|--------------|----------------------------------|  
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|  
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|  
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como interpretar o `unionmember` membro da `TYPE_INFO` estrutura em C#. Este exemplo mostra a interpretação de apenas um tipo ( `TYPE_KIND_METADATA` ), mas os outros são interpretados exatamente da mesma maneira.  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(TYPE_INFO ti)  
        {  
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)  
            {  
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,  
                                               typeof(METADATA_TYPE));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
