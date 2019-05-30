---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0160a14a4ad20e7144e48f767fad88951ca1e473
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318384"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
Especifica os sinalizadores de desmontagem.

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
Indica que essa instrução está em um documento diferente que a anterior.

`DF_DISABLED`\
Indica que essa instrução não será executada.

`DF_INSTRUCTION_ACTIVE`\
Indica que essa instrução é uma das próximas instruções a ser executado (pode haver mais de um).

`DF_DATA`\
Indica que essa instrução é realmente dados (não no código).

`DF_HASSOURCE`\
Indica que essa instrução tem origem. Algumas instruções, como o código de coleta de lixo ou a criação de perfil, não tem nenhum código-fonte correspondente.

`DF_DOCUMENT_CHECKSUM`\
Indica que `bstrDocumentUrl` campo contiver dados de soma de verificação após a URL do documento. Consulte a seção comentários para o [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura para como os dados de soma de verificação são armazenados.

## <a name="remarks"></a>Comentários
Usado como o `dwFlags` membro a [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura.

Esses sinalizadores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
