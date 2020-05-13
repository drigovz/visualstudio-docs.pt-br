---
title: PROVIDER_PROCESS_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713772"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Esta estrutura fornece informações sobre processos em execução em uma máquina.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Membros
 `Fields`\
 Uma combinação de bandeiras da [enumeração PROVIDER_FIELDS,](../../../extensibility/debugger/reference/provider-fields.md) indicando quais campos estão preenchidos.

 `ProgramNodes`\
 Uma estrutura [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) que contém uma matriz de nódulos de programa.

 `fIsDebuggerPresent`\
 Não zero`TRUE`( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ) se o depurador estiver funcionando, zero (`FALSE`) se não estiver.

## <a name="remarks"></a>Comentários
 Essa estrutura é passada para o método [GetProviderProcessData,](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) onde é preenchida.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
