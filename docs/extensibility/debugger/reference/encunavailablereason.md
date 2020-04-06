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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737159"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Representa as razões pelas quais **edite e continue** não está disponível.

## <a name="syntax"></a>Sintaxe

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
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
Nenhuma razão específica para que edite e continue não esteja disponível.

`ENCUN_INTEROP`\
Editar e continuar não está disponível durante uma chamada InterOp.

`ENCUN_SQLCLR`\
Edit and Continue não está disponível durante uma chamada de procedimento SQL que usa o Common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Edite e Continue não esteja disponível durante o processamento de um mini-dump.

`ENCUN_EMBEDDED`\
Edite e Continue não esteja disponível no processamento de código incorporado.

`ENCUN_ATTACH`\
Edit e Continue não estão disponíveis porque a sessão foi anexada, não lançada pelo depurador.

`ENCUN_WIN64`\
Edit e Continue não estão disponíveis durante o processamento do código windows de 64 bits.

## <a name="remarks"></a>Comentários
Esta enumeração é para [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]uso interno apenas por . Os métodos [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) e [DisableENC,](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementados por `E_NOTIMPL`um fornecedor de porto personalizado, devem sempre retornar .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.idl

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
