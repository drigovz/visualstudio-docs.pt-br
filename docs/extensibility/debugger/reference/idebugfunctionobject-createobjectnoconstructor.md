---
title: IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor
helpviewer_keywords:
- IDebugFunctionObject::CreateObjectNoConstructor method
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e6225099b3b88cbbbb73884cbd93be4f7976e50
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200837"
---
# <a name="idebugfunctionobjectcreateobjectnoconstructor"></a>IDebugFunctionObject::CreateObjectNoConstructor
Cria um objeto com nenhum construtor.

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

## <a name="parameters"></a>Parâmetros
`pClassObject`\
[in] Uma [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa o tipo de objeto a ser criado.

`ppObject`\
[out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto recém-criado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que representa uma instância de uma estrutura ou tipo complexo (que não exigem um construtor) que é um parâmetro para a função que é representado pelo [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.

 Se o parâmetro de objeto requer um construtor, chame o [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
- [CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)