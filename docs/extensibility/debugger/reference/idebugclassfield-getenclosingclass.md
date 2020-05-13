---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5a68e32da370d6881eb2b74cbca157f7b899329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734400"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Tem a classe que encerra essa aula.

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

## <a name="parameters"></a>parâmetros
`ppClassField`\
[fora] Retorna um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) representando a classe de fechamento. Retorna um valor nulo se não houver classe de encerramento.

## <a name="return-value"></a>Valor retornado
Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Se a classe representada por este objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) `ppClassField` for uma `IDebugClassField` classe aninhada, o parâmetro reacircunda um objeto representando a classe de fechamento. Por exemplo, dada essa definição de classe:

```
class RootClass {
    class NestedClass { }
};
```

Chamar `GetEnclosingClass` o método `IDebugClassField` no objeto `NestedClass` representando `IDebugClassField` a classe retorna `RootClass`um objeto representando a classe .

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
