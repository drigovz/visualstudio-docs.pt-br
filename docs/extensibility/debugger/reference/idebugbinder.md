---
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735964"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Esta interface liga um campo de símbolo, normalmente retornado pelo provedor de símbolos, a um contexto de memória ou objeto que contém o valor atual do símbolo.

## <a name="syntax"></a>Sintaxe

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface suporta a avaliação de expressão e deve ser implementada pelo mecanismo de depuração (DE).

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é usada no processo de avaliação de expressão e é tipicamente usada na implementação de [AssessSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [AssessAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugBinder`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Associar](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtém o contexto de memória ou objeto que contém o valor atual do símbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina o tipo de tempo de execução de um objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte um local de objeto ou endereço de memória em um contexto de memória.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtém um objeto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) usado para criar parâmetros de função.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtém o tipo exato para uma variável.|

## <a name="remarks"></a>Comentários
 Esta interface retorna objetos que são usados pelo avaliador de expressão em árvores de análise. O avaliador de expressão analisa uma expressão usando o provedor de símbolos para converter os símbolos na expressão em instâncias de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que descrevem cada símbolo em termos de seu tipo e localização no código-fonte. O [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) método Bind `IDebugField` converte objetos em objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que conectam ou vinculam um tipo de símbolo a um valor real na memória. Esses `IDebugObject` objetos são então armazenados em uma árvore de análise para avaliação posterior.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
