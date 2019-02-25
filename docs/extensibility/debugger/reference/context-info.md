---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c41a155fb3a85bcb9f0b0e5eae461f2ae172c7e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709974"
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
dwFields uma combinação de sinalizadores de ele [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeração que especifica quais campos são preenchidos<strong>.</strong>

bstrModuleUrl o nome do módulo no qual o contexto está localizado.

o nome da função onde se encontra o contexto de bstrFunction.

Um de posFunctionOffset [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura que identifica o deslocamento de linha e coluna da função associada com o contexto de código.

bstrAddress o endereço no código onde se encontra o contexto determinado.

bstrAddressOffset o deslocamento do endereço no código onde se encontra o contexto determinado.

bstrAddressAbsolute o endereço absoluto na memória onde se encontra o contexto determinado.

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
