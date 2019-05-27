---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23380106a1c78ba139beec94698bcfa5090c4b08
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200751"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Cria um objeto que usa um construtor que recebe as configurações de sinalizador de avaliação e um valor de tempo limite.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parâmetros
`pConstructor`\
[in] Uma [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa o construtor do objeto a ser criado.

`dwArgs`\
[in] O número de parâmetros no `pArg` matriz. Representa o número de parâmetros passados para o construtor.

`pArgs`\
[in] Uma matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representa os parâmetros passados para o construtor.

`dwEvalFlags`\
[in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que especificam como a avaliação deve ser executada.

`dwTimeout`\
[in] Tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use **infinito** para aguardar indefinidamente.

`ppObject`\
[out] Retorna um **IDebugObject** que representa o objeto recém-criado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que representa uma instância de uma classe ou outro tipo complexo que exige um construtor, que é um parâmetro.

## <a name="see-also"></a>Consulte também
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)