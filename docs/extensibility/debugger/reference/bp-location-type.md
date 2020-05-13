---
title: BP_LOCATION_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_TYPE
helpviewer_keywords:
- BP_LOCATION_TYPE structure
ms.assetid: 0248430a-3b61-4809-87a9-e9b6bb7d1130
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e6bdc0dba8f6bcbdd55c45132dff02735786d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737945"
---
# <a name="bp_location_type"></a>BP_LOCATION_TYPE
Especifica o tipo de localização do ponto de ruptura para uma solicitação de ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
typedef DWORD BP_LOCATION_TYPE;
```

```csharp
public enum enum_BP_LOCATION_TYPE {
    BPLT_NONE               = 0x00000000,
    BPLT_FILE_LINE          = 0x00010000,
    BPLT_FUNC_OFFSET        = 0x00020000,
    BPLT_CONTEXT            = 0x00030000,
    BPLT_STRING             = 0x00040000,
    BPLT_ADDRESS            = 0x00050000,
    BPLT_RESOLUTION         = 0x00060000,
    BPLT_CODE_FILE_LINE     = BPT_CODE | BPLT_FILE_LINE,
    BPLT_CODE_FUNC_OFFSET   = BPT_CODE | BPLT_FUNC_OFFSET,
    BPLT_CODE_CONTEXT       = BPT_CODE | BPLT_CONTEXT,
    BPLT_CODE_STRING        = BPT_CODE | BPLT_STRING,
    BPLT_CODE_ADDRESS       = BPT_CODE | BPLT_ADDRESS ,
    BPLT_DATA_STRING        = BPT_DATA | BPLT_STRING,
    BPLT_TYPE_MASK          = 0x0000FFFF,
    BPLT_LOCATION_TYPE_MASK = 0xFFFF0000
};
```

## <a name="fields"></a>Campos
`BPLT_NONE`\
Não especifica nenhum local de ponto de ruptura.

`BPLT_FILE_LINE`\
Especifica o tipo de localização do ponto de partida como uma linha de arquivo.

`BPLT_FUNC_OFFSET`\
Especifica o tipo de localização do ponto de partida como deslocamento de função.

`BPLT_CONTEXT`\
Especifica o tipo de localização do ponto de ruptura como um contexto.

`BPLT_STRING`\
Especifica o tipo de localização do ponto de partida como uma seqüência de string.

`BPLT_ADDRESS`\
Especifica o tipo de localização do ponto de ruptura como um endereço.

`BPLT_RESOLUTION`\
Especifica o tipo de localização do ponto de partida como uma resolução.

`BPLT_CODE_FILE_LINE`\
Especifica o tipo de localização do ponto de ruptura como uma linha de código fonte.

`BPLT_CODE_FUNC_OFFSET`\
Especifica o tipo de localização do ponto de ruptura como deslocamento da função de código.

`BPLT_CODE_CONTEXT`\
Especifica o tipo de localização do ponto de ruptura como um contexto de código.

`BPLT_CODE_STRING`\
Especifica o tipo de localização do ponto de ruptura como uma seqüência de código.

`BPLT_CODE_ADDRESS`\
Especifica o tipo de localização do ponto de ruptura como um endereço de código.

`BPLT_DATA_STRING`\
Especifica o tipo de localização do ponto de partida como uma seqüência de dados.

`BPLT_TYPE_MASK`\
Especifica uma máscara de bit, para que o tipo de ponto de ruptura possa ser extraído do valor.

`BPLT_LOCATION_TYPE_MASK`\
Especifica uma máscara de bit, para que o tipo de localização de ponto de ruptura possa ser extraído do valor.

## <a name="remarks"></a>Comentários
Passou como parâmetro para o método [GetLocationType.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)

Um tipo de local de ponto de ruptura é composto por um tipo de ponto de ruptura e um tipo de local. Isso significa que um tipo de local de ponto de `BPT_CODE`ruptura nunca é apenas `BPLT_FILE_LINE`um tipo de ponto de ruptura (por exemplo, ) ou um tipo de local (por exemplo, ). As constantes predefinidas para todos os tipos de localização de`BPLT_CODE_FILE_LINE` `BPLT_DATA_STRING`ponto de ruptura atualmente suportados estão incluídas nesta enumeração (através ).

`BPT_CODE`e `BPT_DATA` são membros da [enumeração BP_TYPE.](../../../extensibility/debugger/reference/bp-type.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
