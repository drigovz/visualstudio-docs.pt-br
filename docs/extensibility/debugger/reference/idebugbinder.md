---
title: IDebugBinder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4e5588006fb8991d5560ddfad95d41d39db7c33
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414057"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Essa interface é associado a um campo de símbolo, normalmente é retornado pelo provedor de símbolo, a um contexto de memória ou um objeto que contém o valor atual do símbolo.

## <a name="syntax"></a>Sintaxe

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Esta interface dá suporte à avaliação de expressão e deve ser implementada pelo mecanismo de depuração (DES).

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é usada no processo de avaliação de expressão e normalmente é usada na implementação de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugBinder`.

|Método|Descrição|
|------------|-----------------|
|[Associar](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtém o contexto de memória ou um objeto que contém o valor atual do símbolo.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Determina o tipo de tempo de execução de um objeto.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Converte um endereço de memória ou o local do objeto em um contexto de memória.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtém uma [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto usado para criar parâmetros de função.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtém o tipo exato para uma variável.|

## <a name="remarks"></a>Comentários
 Essa interface retorna objetos que são usados pelo avaliador de expressão em analisar árvores. O avaliador de expressão analisa uma expressão, usando o provedor de símbolo para converter os símbolos na expressão para instâncias do [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), que descrevem cada símbolo em termos de seu tipo e o local no código-fonte. O [vincular](../../../extensibility/debugger/reference/idebugbinder-bind.md) método converte `IDebugField` objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que se conectar ou associar um símbolo de tipo para um valor real na memória. Eles `IDebugObject` objetos, em seguida, são armazenados em uma árvore de análise para avaliação posterior.

## <a name="requirements"></a>Requisitos
 Cabeçalho: ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Interfaces de Avaliação de Expressões](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)