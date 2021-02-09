---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91a4e04e26a57247a541c565ea4f0f392a413d39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925058"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtém a classe que inclui essa classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetEnclosingClass(
    IDebugClassField** ppClassField
);
```

```csharp
int GetEnclosingClass(
    out IDebugClassField ppClassField
);
```

## <a name="parameters"></a>Parâmetros
`ppClassField`\
fora Retorna um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa a classe delimitadora. Retorna um valor nulo se não houver nenhuma classe delimitadora.

## <a name="return-value"></a>Valor retornado
Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Se a classe representada por esse objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) for uma classe aninhada, o `ppClassField` parâmetro retornará um `IDebugClassField` objeto que representa a classe de circunscrição. Por exemplo, dada essa definição de classe:

```
class RootClass {
    class NestedClass { }
};
```

Chamar o `GetEnclosingClass` método no `IDebugClassField` objeto que representa a `NestedClass` classe retorna um `IDebugClassField` objeto que representa a classe `RootClass` .

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
