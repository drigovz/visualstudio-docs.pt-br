---
title: IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad95f9273276830b59ebc77214f3920a687d41ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728566"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Cria um objeto sem construtor.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateObjectNoConstructor( 
   IDebugField*   pClassObject,
   IDebugObject** ppObject
);
```

```csharp
int CreateObjectNoConstructor(
   IDebugField      pClassField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>parâmetros
`pClassObject`\
[em] Um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) representando o tipo do objeto a ser criado.

`ppObject`\
[fora] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) representando o objeto recém-criado.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame este método para criar um objeto que represente uma instância de uma estrutura ou tipo complexo (que não requer um construtor) que seja um parâmetro para a função representada pela interface [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

 Se o parâmetro de objeto exigir um construtor, chame o método [CreateObject.](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)

## <a name="see-also"></a>Confira também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)
