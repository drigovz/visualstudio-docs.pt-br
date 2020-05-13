---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729786"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
O mecanismo de depuração (DE) envia essa interface para o Gerenciador de depuração de sessão (SDM) quando uma exceção é lançada no programa que está sendo executado.

## <a name="syntax"></a>Sintaxe

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa esta interface para informar que ocorreu uma exceção no programa que está sendo depurado. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface. O SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia este objeto de evento para relatar uma exceção. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando anexada ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugExceptionEvent2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtém informações detalhadas sobre a exceção que demitiu este evento.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtém uma descrição de humanos para a exceção lançada que disparou este evento.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se o mecanismo de depuração (DE) suporta ou não a opção de passar essa exceção ao programa que está sendo depurado quando a execução é retomada.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica se a exceção deve ser transmitida ao programa que está sendo depurado quando a execução é retomada ou se a exceção deve ser descartada.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Comentários
 Antes de enviar o evento, o DE verifica se esse evento de exceção foi designado como uma exceção de primeira ou segunda chance por uma chamada anterior para [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Se ele foi designado para ser uma exceção de primeira chance, o `IDebugExceptionEvent2` evento é enviado para o SDM. Caso assim, o DE dê ao aplicativo a chance de lidar com a exceção. Se nenhum manipulador de exceção for fornecido e se a exceção `IDebugExceptionEvent2` tiver sido designada como uma exceção de segunda chance, o evento será enviado para o SDM. Caso contrário, o DE retoma a execução do programa, e o sistema operacional ou tempo de execução lida com a exceção.

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
