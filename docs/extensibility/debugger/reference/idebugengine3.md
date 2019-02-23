---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c043a05d2656dc1cc56377ad061854cd1aca9e7c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709532"
---
# <a name="idebugengine3"></a>IDebugEngine3
Representa um mecanismo de depuração único (DES) que controla a depuração de um ou mais módulos.

## <a name="syntax"></a>Sintaxe

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada por um DE personalizado (se ele dá suporte a símbolos) para habilitar o estado de JustMyCode. Esta interface deve ser implementada por DE se ele dá suporte a símbolos e JustMyCode.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é chamada pelo Gerenciador de depuração de sessão (SDM) para passar opções de usuário para locais de onde carregar os símbolos. Ele também é chamado para definir o GUID do mecanismo de quando ela é instanciada (esse GUID com base nas métricas do momento do mecanismo de registro). O SDM também chama essa interface para definir o estado de JustMyCode e definir todas as exceções conhecidas pelo depurador para um estado especificado.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos herdados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), o `IDebugEngine3` interface expõe os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Define o caminho ou caminhos que o DE será usado para procurar símbolos de depuração.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carrega os símbolos para todos os módulos que ainda não tiveram seus símbolos carregados.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informa o DE sobre as informações de JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Define o GUID DE métricas.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Defina todas as exceções pendente no momento para um estado especificado.|

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)