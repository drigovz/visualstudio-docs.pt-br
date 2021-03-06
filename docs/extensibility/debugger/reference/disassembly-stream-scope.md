---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 54773ee6f770855122992f49bebad44fa1f6129a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870292"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Especifica o escopo do fluxo de desmontagem.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Campos
`DSS_HUGE`\
Especifica que a desmontagem do contexto de código geraria mais saída do que um cliente normalmente desejaria recuperar em uma única chamada.

`DSS_FUNCTION`\
Especifica que a função contida no contexto de código deve ser desmontada. Especifica que o fluxo de desmontagem representa uma função, quando retornado pelo método [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

`DSS_MODULE`\
Quando retornado pelo `IDebugDisassemblyStream2::GetScope` método, especifica que o fluxo de desmontagem representa um módulo.

`DSS_ALL`\
Especifica a desmontagem para todo o espaço de endereço.

## <a name="remarks"></a>Comentários
Passado como um argumento para o método [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) e retornado pelo método [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

Esses valores podem ser combinados com um bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
