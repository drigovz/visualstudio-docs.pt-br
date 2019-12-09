---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6927a63241e2f2794fb5c70945962e00a1676431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329495"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Obtém a classe que engloba essa classe.

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
[out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) a classe de objeto que representa o delimitador. Retorna um valor nulo se não houver nenhuma classe delimitadora.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
Se a classe representada por este [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto é uma classe aninhada, em seguida, a `ppClassField` parâmetro retorna um `IDebugClassField` a classe de objeto que representa o delimitador. Por exemplo, dada esta definição de classe:

```
class RootClass {
    class NestedClass { }
};
```

Chamando o `GetEnclosingClass` método em de `IDebugClassField` objeto que representa o `NestedClass` classe retorna um `IDebugClassField` que representa a classe de objeto `RootClass`.

## <a name="see-also"></a>Consulte também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
