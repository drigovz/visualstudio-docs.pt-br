---
title: IDebugExceptionEvent2::GetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79385348aa9290f26a34b99dbd2d6f68cb92dc8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920220"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Obtém uma descrição detalhada da exceção que disparou este evento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

#### <a name="parameters"></a>Parâmetros
 `pExceptionInfo`

 [no, out] Uma [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura será preenchida com a descrição da exceção.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

 [C++ somente] O chamador é responsável por liberar quaisquer cadeias de caracteres na [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) estrutura, bem como liberar a [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto na estrutura.

## <a name="see-also"></a>Consulte também
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)