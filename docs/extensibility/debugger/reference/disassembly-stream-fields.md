---
title: DISASSEMBLY_STREAM_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fdc4a738a28f64aa87955f339409d1e64ed3bd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715668"
---
# <a name="disassemblystreamfields"></a>DISASSEMBLY_STREAM_FIELDS
Especifica quais informações devem ser recuperadas sobre um campo de desmontagem.

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

## <a name="members"></a>Membros
DSF_ADDRESS Initialize/usar o `bstrAddress` campo.

DSF_ADDRESSOFFSET Initialize/usar o `bstrAddressOffset` campo.

DSF_CODEBYTES Initialize/usar o `bstrCodeBytes` campo.

DSF_OPCODE Initialize/usar o `bstrOpCode` campo.

DSF_OPERANDS Initialize/usar o `bstrOperands` campo.

DSF_SYMBOL Initialize/usar o `bstrSymbol` campo.

DSF_CODELOCATIONID Initialize/usar o `uCodeLocationId` campo.

DSF_POSITION Initialize/usar o `posBeg` e `posEnd` campos.

DSF_DOCUMENTURL Initialize/usar o `bstrDocumentUrl` campo.

DSF_BYTEOFFSET Initialize/usar o `dwByteOffset` campo.

DSF_FLAGS Initialize/usar o `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) campo.

Os nomes de símbolo DSF_OPERANDS_SYMBOLS incluem no `bstrOperands` campo.

DSF_ALL especifica todos os campos para o fluxo de desmontagem.

## <a name="remarks"></a>Comentários
Passado como um parâmetro para o [leitura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método para indicar quais campos da [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) são de estrutura a ser inicializado.

Usado para o `dwFields` membro o `DisassemblyData` estrutura para indicar quais campos são usados e válidos quando a estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Ler](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
