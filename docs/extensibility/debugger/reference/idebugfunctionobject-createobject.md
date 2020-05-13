---
title: IDebugFunctionObject::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: beb00bcf932b19ed4e489456236957c55d909ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728601"
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Cria um objeto usando um construtor.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateObject( 
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject(
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   out IDebugObject     ppObject
);
```

## <a name="parameters"></a>parâmetros
`pConstructor`\
[em] Um objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) representando o construtor do objeto a ser criado.

`dwArgs`\
[em] O número de `pArg` parâmetros na matriz. Representa o número de parâmetros passados para o construtor.

`pArg`\
[em] Uma matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) representando os parâmetros passados para o construtor.

`ppObject`\
[fora] Retorna `IDebugObject` um representando o objeto recém-criado.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame este método para criar um objeto que represente uma instância de uma classe (ou outro tipo complexo que requer um construtor) que seja um parâmetro para a função representada pela interface [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Se o parâmetro de objeto não exigir um construtor, chame o método [CreateObjectNoConstructor.](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
