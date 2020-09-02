---
title: 'IDebugFunctionObject:: CreateObject | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
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

## <a name="parameters"></a>Parâmetros
`pConstructor`\
no Um objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) que representa o construtor do objeto a ser criado.

`dwArgs`\
no O número de parâmetros na `pArg` matriz. Representa o número de parâmetros passados para o construtor.

`pArg`\
no Uma matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa os parâmetros passados para o construtor.

`ppObject`\
fora Retorna um `IDebugObject` representando o objeto recém-criado.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que represente uma instância de uma classe (ou outro tipo complexo que exija um construtor) que seja um parâmetro para a função que é representada pela interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

 Se o parâmetro de objeto não exigir um construtor, chame o método [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) .

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
