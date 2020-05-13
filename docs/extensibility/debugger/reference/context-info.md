---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4838df34c14b936af15b8a7a582a6d30ea12bee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737574"
---
# <a name="context_info"></a>CONTEXT_INFO
Esta estrutura descreve um contexto de memória ou contexto de código.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>Membros
`dwFields`\
Uma combinação de bandeiras de ele [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeração que especifica quais campos são<strong>preenchidos.</strong>

`bstrModuleUrl`\
O nome do módulo onde o contexto está localizado.

`bstrFunction`\
O nome da função onde o contexto está localizado.

`posFunctionOffset`\
Uma [estrutura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que identifica a linha e a coluna offset da função associada ao contexto do código.

`bstrAddress`\
O endereço em código onde o contexto dado está localizado.

`bstrAddressOffset`\
A compensação do endereço em código onde o contexto dado está localizado.

`bstrAddressAbsolute`\
O endereço absoluto na memória onde o contexto dado está localizado.

## <a name="remarks"></a>Comentários
Essa estrutura é devolvida a partir de uma chamada para o método [GetInfo.](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)

Um uso típico para esta estrutura é no suporte a uma janela de depuração de **memória.**

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
