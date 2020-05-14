---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730656"
---
# <a name="idebugengine3"></a>IDebugEngine3
Representa um único mecanismo de depuração (DE) que controla a depuração de um ou mais módulos.

## <a name="syntax"></a>Sintaxe

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por um DE personalizado (se ele suporta símbolos) para habilitar o estado JustMyCode. Esta interface deve ser implementada pelo DE se ele suporta símbolos e JustMyCode.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é chamada pelo Session Debug Manager (SDM) para passar as opções do usuário para locais dos quais carregar símbolos. Ele também é chamado para definir o GUID do motor quando ele é instancidado (este GUID é baseado nas métricas do momento do registro do motor). O SDM também chama essa interface para definir o estado JustMyCode e definir todas as exceções conhecidas pelo depurador para um estado especificado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos herdados do [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md)a `IDebugEngine3` interface expõe os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Define os caminhos ou caminhos que o DE usará para procurar símbolos de depuração.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carrega os símbolos para todos os módulos que ainda não tiveram seus símbolos carregados.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informa o DE sobre as informações do JustMyCode.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Define o GUIA DE a partir das métricas.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Defina todas as exceções atualmente pendentes para um estado especificado.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
