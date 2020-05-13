---
title: IDebugExceptionEvent2:CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729876"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se o mecanismo de depuração (DE) suporta ou não a opção de passar essa exceção ao programa que está sendo depurado quando a execução é retomada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valor retornado
 Devoluções (a `S_OK` exceção pode ser `S_FALSE` passada para o programa) ou (a exceção não pode ser transmitida).

## <a name="remarks"></a>Comentários
 O DE deve ter uma ação padrão para passar para a depuração. O IDE pode receber o evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e `CanPassToDebuggee` chamar o método [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) sem chamar o método. Portanto, o DE deve ter um caso padrão para passar a exceção ou não.

## <a name="see-also"></a>Confira também
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
