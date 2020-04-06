---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d86997d11e124fd5a47981314cf383f5cd8aff7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719473"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
Esta interface estende [o IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para lidar com exceções interceptadas.

## <a name="syntax"></a>Sintaxe

```
IDebugStackFrame3 : IDebugStackFrame2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O depurador (DE) implementa essa interface no mesmo objeto que implementa a interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para suportar exceções interceptadas.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para o `IDebugStackFrame2` [QueryInterface](/cpp/atl/queryinterface) em uma interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) `IDebugStackFrame3` expõe os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Lida com uma exceção para o quadro de pilha atual antes de qualquer tratamento regular de exceção.|
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retorna um contexto de código se uma pilha descontrair ocorrer.|

## <a name="remarks"></a>Comentários
 Uma exceção interceptada significa que um depurador pode processar uma exceção antes que qualquer rotina normal de manipulação de exceções seja chamada pelo tempo de execução. Interceptar uma exceção significa essencialmente fazer o tempo de execução fingir que há um manipulador de exceção presente mesmo quando não há.

- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) é chamado durante todos os eventos normais de retorno de chamada de exceção (a única exceção a isso é se você estiver depurando código de modo misto (código gerenciado e não gerenciado), nesse caso a exceção não pode ser interceptada durante a chamada de última chance). Se o DE não `IDebugStackFrame3`implementar ou o DE retornar um erro do`InterceptCurrentException` IDebugStackFrame3:: (como) `E_NOTIMPL`o depurador lidará com a exceção normalmente.

 Ao interceptar uma exceção, o depurador pode permitir que o usuário faça alterações no estado do programa que está sendo depurado e, em seguida, retomar a execução no ponto em que a exceção foi lançada.

> [!NOTE]
> Exceções interceptadas são permitidas apenas em código gerenciado, ou seja, em um programa que está sendo executado sob o Common Language Runtime (CLR).

 Um mecanismo de depuração indica que ele suporta interceptar exceções definindo "metricExceptions" `SetMetric` para um valor de 1 no tempo de execução usando a função. Para obter mais informações, consulte [os ajudantes do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
