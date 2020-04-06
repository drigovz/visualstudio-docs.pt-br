---
title: IDebugFunctionObject2:CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728484"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Cria um objeto que usa um construtor dado configurações de sinalizador de avaliação e um valor de tempo.

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

## <a name="parameters"></a>parâmetros
`pConstructor`\
[em] Um objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa o construtor do objeto a ser criado.

`dwArgs`\
[em] O número de `pArg` parâmetros na matriz. Representa o número de parâmetros passados para o construtor.

`pArgs`\
[em] Uma matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa os parâmetros passados para o construtor.

`dwEvalFlags`\
[em] Uma combinação de bandeiras da [enumeração EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifica como a avaliação deve ser realizada.

`dwTimeout`\
[em] Tempo máximo, em milissegundos, para esperar antes de retornar deste método. Use **INFINITE** para esperar indefinidamente.

`ppObject`\
[fora] Retorna um **IDebugObject** representando o objeto recém-criado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame este método para criar um objeto que represente uma instância de uma classe, ou outro tipo complexo que exija um construtor, que é um parâmetro.

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
