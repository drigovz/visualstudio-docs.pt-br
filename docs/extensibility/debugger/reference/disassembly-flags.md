---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737378"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
Especifica as bandeiras para desmontagem.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>Campos
`DF_DOCUMENTCHANGE`\
Indica que esta instrução está em um documento diferente do anterior.

`DF_DISABLED`\
Indica que esta instrução não será executada.

`DF_INSTRUCTION_ACTIVE`\
Indica que esta instrução é uma das próximas instruções a serem executadas (pode haver mais de uma).

`DF_DATA`\
Indica que esta instrução é realmente dados (não código).

`DF_HASSOURCE`\
Indica que esta instrução tem origem. Algumas instruções, como perfil ou código de coleta de lixo, não têm fonte correspondente.

`DF_DOCUMENT_CHECKSUM`\
Indica `bstrDocumentUrl` que o campo contém dados de soma de cheques após a URL do documento. Consulte a seção Observações para a estrutura [DesassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) para saber como os dados do soma de verificação são armazenados.

## <a name="remarks"></a>Comentários
Usado como `dwFlags` membro da estrutura [DesassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
