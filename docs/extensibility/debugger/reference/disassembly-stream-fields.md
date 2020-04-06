---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737361"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
Especifica quais informações recuperar sobre um campo de desmontagem.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>Campos
`DSF_ADDRESS`\
Inicializar/usar `bstrAddress` o campo.

`DSF_ADDRESSOFFSET`\
Inicializar/usar `bstrAddressOffset` o campo.

`DSF_CODEBYTES`\
Inicializar/usar `bstrCodeBytes` o campo.

`DSF_OPCODE`\
Inicializar/usar `bstrOpCode` o campo.

`DSF_OPERANDS`\
Inicializar/usar `bstrOperands` o campo.

`DSF_SYMBOL`\
Inicializar/usar `bstrSymbol` o campo.

`DSF_CODELOCATIONID`\
Inicializar/usar `uCodeLocationId` o campo.

`DSF_POSITION`\
Inicializar/usar `posBeg` os `posEnd` campos e.

`DSF_DOCUMENTURL`\
Inicializar/usar `bstrDocumentUrl` o campo.

`DSF_BYTEOFFSET`\
Inicializar/usar `dwByteOffset` o campo.

`DSF_FLAGS`\
Inicialize/use `dwFlags` o campo[(DISASSEMBLY_FLAGS).](../../../extensibility/debugger/reference/disassembly-flags.md)

`DSF_OPERANDS_SYMBOLS`\
Inclua nomes de `bstrOperands` símbolos no campo.

`DSF_ALL`\
Especifica todos os campos para o fluxo de desmontagem.

## <a name="remarks"></a>Comentários
Passou como parâmetro para o método [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) para indicar quais campos da estrutura [DesassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) devem ser inicializados.

Usado para `dwFields` o `DisassemblyData` membro da estrutura para indicar quais campos são usados e válidos quando a estrutura é devolvida.

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Ler](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
