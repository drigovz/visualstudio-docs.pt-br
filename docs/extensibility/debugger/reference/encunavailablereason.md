---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 384d71d6f88e8cd792585bb097594fa7b1e38c64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953741"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Representa os motivos pelos quais **Editar e continuar** não estão disponíveis.

## <a name="syntax"></a>Sintaxe

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Campos
`ENCUN_NONE`\
Nenhum motivo específico pelo qual editar e continuar não está disponível.

`ENCUN_INTEROP`\
Editar e continuar não está disponível durante uma chamada de interoperabilidade.

`ENCUN_SQLCLR`\
Editar e continuar não está disponível durante uma chamada de procedimento SQL que usa o CLR (Common Language Runtime).

`ENCUN_MINIDUMP`\
Editar e continuar não está disponível durante o processamento de um mini-despejo.

`ENCUN_EMBEDDED`\
Editar e continuar não está disponível durante o processamento de código inserido.

`ENCUN_ATTACH`\
Editar e continuar não está disponível porque a sessão foi anexada a, não iniciada pelo, o depurador.

`ENCUN_WIN64`\
Editar e continuar não está disponível durante o processamento do código do Windows de 64 bits.

## <a name="remarks"></a>Comentários
Essa enumeração é para uso interno apenas pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Os métodos [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) , conforme implementados por um fornecedor de porta personalizada, sempre devem retornar `E_NOTIMPL` .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. idl

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
