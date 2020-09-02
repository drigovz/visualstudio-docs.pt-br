---
title: 'IDebugFunctionObject:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529a5f67c808efa258bc0cb9899f546dbb90d431
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728502"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Chama a função e retorna o valor resultante como um objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parâmetros
`ppParams`\
no Uma matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa os parâmetros de entrada. Cada um desses parâmetros foi criado com um dos `Create` métodos na interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

`dwParams`\
no O número de parâmetros na `ppParams` matriz.

`dwTimeout`\
no Especifica o tempo máximo, em milissegundos, a aguardar antes de retornar desse método. Use `INFINITE` para aguardar indefinidamente.

`ppResult`\
fora Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o valor da função como um objeto.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método configura e executa uma chamada para a função representada pelo objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
