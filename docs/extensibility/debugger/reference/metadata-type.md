---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5aa21d4bfccd50e31c2fd7e76bb8808bba19bc58
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333744"
---
# <a name="metadatatype"></a>METADATA_TYPE
Essa estrutura Especifica informações sobre um tipo de campo tirado de metadados.

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

## <a name="parameters"></a>Parâmetros
 `ulAppDomainID`\
 ID do aplicativo do qual o símbolo foi originada. Isso é usado para identificar exclusivamente uma instância do aplicativo.

 `guidModule`\
 O GUID do módulo que contém esse campo.

 `tokClass`\
 A ID do token metadados desse tipo.

 [C++] `_mdToken` é um `typedef` de 32 bits `int`.

## <a name="remarks"></a>Comentários
 Essa estrutura é exibido como parte da união na [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estrutura quando o `dwKind` campo dos `TYPE_INFO` estrutura é definida como `TYPE_KIND_METADATA` (um valor da [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração).

 O `tokClass` valor é um token de metadados que identifica exclusivamente um tipo. Para obter detalhes sobre como interpretar os bits superiores do que a ID do token de metadados, consulte a `CorTokenType` enumeração no arquivo corhdr. h no [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.

## <a name="requirements"></a>Requisitos
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)