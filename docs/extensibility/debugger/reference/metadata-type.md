---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714301"
---
# <a name="metadata_type"></a>METADATA_TYPE
Esta estrutura especifica informações sobre um tipo de campo extraído de metadados.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>parâmetros
 `ulAppDomainID`\
 ID do aplicativo de onde veio o símbolo. Isso é usado para identificar exclusivamente uma instância do aplicativo.

 `guidModule`\
 O GUID do módulo que contém este campo.

 `tokClass`\
 O ID de token de dados de metadados deste tipo.

 [C++] `_mdToken` é `typedef` um para um `int`de 32 bits .

## <a name="remarks"></a>Comentários
 Essa estrutura aparece como parte da união `dwKind` na estrutura `TYPE_INFO` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando `TYPE_KIND_METADATA` o campo da estrutura é definido para (um valor da [enumeração dwTYPE_KIND).](../../../extensibility/debugger/reference/dwtype-kind.md)

 O `tokClass` valor é um token de metadados que identifica exclusivamente um tipo. Para obter detalhes sobre como interpretar os bits superiores `CorTokenType` do ID de token de metadados, consulte a enumeração no arquivo corhdr.h no .NET Framework SDK.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
