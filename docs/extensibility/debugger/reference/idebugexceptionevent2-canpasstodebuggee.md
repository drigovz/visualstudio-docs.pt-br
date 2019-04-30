---
title: IDebugExceptionEvent2::CanPassToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93652efe19096466c853d758cc36aa022236068d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920109"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Determina se o mecanismo de depuração (DES) oferece suporte a opção de passar essa exceção para o programa que está sendo depurado quando a execução é retomada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Valor de retorno
 Retorna um `S_OK` (a exceção pode ser passada para o programa) ou `S_FALSE` (a exceção não pode ser passada).

## <a name="remarks"></a>Comentários
 O DE deve ter uma ação padrão para passar para o elemento a ser depurado. O IDE pode receber o [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) evento e a chamada a [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método sem chamar o `CanPassToDebuggee` método. Portanto, o DE deve ter um caso de padrão para transmitir a exceção na ou não.

## <a name="see-also"></a>Consulte também
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)