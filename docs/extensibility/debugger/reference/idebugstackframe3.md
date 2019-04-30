---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d790c7b278d36395c0df5575ed3bc7c381753fe
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412560"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Essa interface estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para lidar com exceções interceptadas.

## <a name="syntax"></a>Sintaxe

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface no mesmo objeto que implementa o [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interface para oferecer suporte a exceções interceptadas.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chame [QueryInterface](/cpp/atl/queryinterface) em um `IDebugStackFrame2` interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos herdados de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` expõe os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Trata a exceção para o quadro de pilha atual antes de qualquer tratamento de exceção regular.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retorna um contexto de código se um desenrolamento de pilha ocorrer.|

## <a name="remarks"></a>Comentários
 Uma exceção interceptada significa que um depurador pode processar uma exceção antes de quaisquer rotinas de manipulação de exceção normal são chamadas pelo tempo de execução. Interceptar uma exceção, essencialmente, significa fazer com que o tempo de execução fingir que há um manipulador de exceção presente até mesmo quando não existe.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) é chamado durante a todos os eventos de retorno de chamada de exceção normal (a única exceção é se você estiver depurando código de modo misto (gerenciado e código não gerenciado), caso em que a exceção não pode ser interceptada durante o última chance retorno de chamada). Se o DE implementar `IDebugStackFrame3`, ou o DE retorna um erro de IDebugStackFrame3::`InterceptCurrentException` (como `E_NOTIMPL`), em seguida, o depurador tratará a exceção normalmente.

 Interceptando uma exceção, o depurador pode permitir que o usuário faça alterações para o estado do programa que está sendo depurado e, em seguida, retomar a execução no ponto onde a exceção foi lançada.

> [!NOTE]
> Exceções interceptadas são permitidas apenas em código gerenciado, ou seja, em um programa que está sendo executado sob o tempo de execução do CLR (Common Language).

 Um mecanismo de depuração indica que ele dá suporte a interceptação exceções definindo "metricExceptions" para um valor de 1 em tempo de execução, usando o `SetMetric` função. Para obter mais informações, consulte [auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)