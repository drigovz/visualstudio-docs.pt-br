---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c50d5ea930f05d22b68416978909cceca17727d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346460"
---
# <a name="contextinfo"></a>CONTEXT_INFO
Essa estrutura descreve um contexto de memória ou o contexto de código.

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
Uma combinação de sinalizadores de ele [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeração que especifica quais campos são preenchidos<strong>.</strong>

`bstrModuleUrl`\
O nome do módulo no qual o contexto está localizado.

`bstrFunction`\
O nome da função onde se encontra o contexto.

`posFunctionOffset`\
Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que identifica o deslocamento de linha e coluna da função associada com o contexto de código.

`bstrAddress`\
O endereço no código onde se encontra o contexto determinado.

`bstrAddressOffset`\
O deslocamento do endereço no código onde se encontra o contexto determinado.

`bstrAddressAbsolute`\
O endereço absoluto na memória onde se encontra o contexto determinado.

## <a name="remarks"></a>Comentários
Essa estrutura é retornada de uma chamada para o [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método.

Um uso típico para esta estrutura é suportados uma **memória** janela de depuração.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
