---
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29756b3be6d2c46d39b581dd3db0af61bfaa18f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878923"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Remove a exceção especificada para que ela não seja mais manipulada pelo mecanismo de depuração.

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

## <a name="parameters"></a>Parâmetros
`pException`\
no Uma estrutura de [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) que descreve a exceção a ser removida.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A exceção que está sendo removida deve ter sido definida anteriormente por uma chamada anterior para o método [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Para remover todas as exceções de conjunto de uma só vez, chame o método [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
