---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80f345d7c6f3ed83d9f33206631a5a5327131a76
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457536"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando uma propriedade que está associada um documento específico está prestes a ser destruído.

## <a name="syntax"></a>Sintaxe

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O DE implementa essa interface para relatar que uma propriedade tiver sido destruída. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface. Usa o SDM [QueryInterface](/cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface. Essa interface é implementada, se o DE anteriormente tiver criado uma propriedade associada a um script; Destruindo a propriedade remove o script associado do IDE.

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia esse objeto de evento para relatório de que uma propriedade tiver sido destruída. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra o método de `IDebugPropertyDestroyEvent2`.

|Método|Descrição|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Obtém a propriedade a ser destruído.|

## <a name="remarks"></a>Comentários
 Consulte os comentários para [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) para obter detalhes sobre por que esses eventos são usados.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)