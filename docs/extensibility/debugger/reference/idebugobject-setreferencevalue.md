---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726371"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Define o valor de referência deste objeto.

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

## <a name="parameters"></a>parâmetros
`pObject`\
[em] Um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) representando o novo valor de referência.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método faz deste objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) uma referência ao `pObject` valor do objeto dado no parâmetro, jogando fora qualquer referência anterior. Observe que `IDebugObject` este objeto já deve ser um tipo de referência.

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
