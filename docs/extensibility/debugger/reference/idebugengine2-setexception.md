---
title: IDebugEngine2::SetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5146b730e6e58e99c22f73bd95cd500e5450ac06
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207555"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Especifica como o mecanismo de depuração (DES) deve lidar com uma determinada exceção.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parâmetros
`pException`\
[in] Uma [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura que descreve a exceção e como depurá-lo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A DE podia ser instruída para interromper o programa gerar uma exceção em primeira chance, segunda chance, ou nenhum.

## <a name="see-also"></a>Consulte também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)