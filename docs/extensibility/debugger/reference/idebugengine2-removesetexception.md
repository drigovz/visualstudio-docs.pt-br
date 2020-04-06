---
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730927"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Remove a exceção especificada para que não seja mais manuseada pelo motor de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>parâmetros
`pException`\
[em] Uma estrutura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) que descreve a exceção a ser removida.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A exceção a ser removida deve ter sido previamente definida por uma chamada anterior para o método [SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md)

 Para remover todas as exceções definidas de uma só vez, chame o método [RemoveAllSetExceptions.](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
