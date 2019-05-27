---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e861a67ada36bd25b30e08bf8a62163bceea979
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211308"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Define o valor de referência do objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parâmetros
`pObject`\
[in] Uma [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o novo valor de referência.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método faz isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto uma referência para o valor do objeto fornecido no `pObject` parâmetro, descartando qualquer referência anterior. Observe que este `IDebugObject` objeto já deve ser um tipo de referência.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)