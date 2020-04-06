---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720657"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Esta interface permite que o SDM (Session Debug Manager, gerenciador de depuração de sessão) recupere uma interface que representa o mecanismo de depuração (DE).

## <a name="syntax"></a>Sintaxe

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa essa interface nos objetos que implementam as interfaces DE mais comuns (como [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)e [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) para permitir o acesso à interface [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) do próprio DE.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamada [QueryInterface](/cpp/atl/queryinterface) em uma interface DE típica para obter esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugQueryEngine2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtém uma interface de mecanismo de depuração personalizada (DE).|

## <a name="remarks"></a>Comentários
 Essa interface é normalmente implementada no objeto que implementa a interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para suportar a saída ordenada por causalidade através de funções; ou seja, quando o depurador está saindo de uma função, a próxima função a ser executada pode não ser a função anterior na pilha, mas uma função em outro segmento completamente. Para obter uma definição de "causalidade", consulte o [Glossário de depurador do Estúdio Visual](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
