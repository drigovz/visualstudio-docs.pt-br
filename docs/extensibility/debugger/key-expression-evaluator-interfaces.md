---
title: Principais interfaces avaliadoras de expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738494"
---
# <a name="key-expression-evaluator-interfaces"></a>Principais interfaces avaliadoras de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ao escrever um avaliador de expressão (EE), juntamente com o contexto de avaliação, você deve estar familiarizado com as seguintes interfaces.

## <a name="interface-descriptions"></a>Descrições de interface

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Tem um único método, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtém uma estrutura de dados que representa o ponto de execução atual. Essa estrutura de dados é um dos três argumentos que o mecanismo de depuração (DE) passa para o método [AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para avaliar uma expressão. Esta interface é normalmente implementada pelo provedor de símbolos.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Tem o método [Bind,](../../extensibility/debugger/reference/idebugbinder-bind.md) que obtém a área de memória que contém o valor atual de um símbolo. Dado o método de contenção, representado por um objeto [IDebugObject,](../../extensibility/debugger/reference/idebugobject.md) e o `IDebugBinder::Bind` próprio símbolo, representado por um objeto [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) retorna o valor do símbolo. `IDebugBinder`é tipicamente implementado pelo DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Representa um simples tipo de dados. Para tipos mais complexos, como arrays e métodos, use as interfaces [Derivada IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) e [IDebugMethodField,](../../extensibility/debugger/reference/idebugmethodfield.md) respectivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) é outra interface derivada importante que representa símbolos contendo outros símbolos, como métodos ou classes. A `IDebugField` interface (e seus derivados) é tipicamente implementada pelo provedor de símbolos.

     Um `IDebugField` objeto pode ser usado para encontrar o nome e o tipo de um símbolo e, juntamente com um objeto [IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) pode ser usado para encontrar seu valor.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Representa os bits reais do valor de tempo de execução de um símbolo. [Vincular](../../extensibility/debugger/reference/idebugbinder-bind.md) pega um objeto [IDebugField,](../../extensibility/debugger/reference/idebugfield.md) que representa um símbolo, e retorna um objeto [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md) O método [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) retorna o valor do símbolo em um buffer de memória. Um DE normalmente implementa essa interface para representar o valor de uma propriedade na memória.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Esta interface representa o próprio avaliador de expressão. O método-chave é [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que retorna uma interface [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Esta interface representa uma expressão parsed pronta para ser avaliada. O método-chave é [O EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que retorna um IDebugProperty2 representando o valor e o tipo da expressão.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Esta interface representa um valor e seu tipo e é o resultado de uma avaliação de expressão.

## <a name="see-also"></a>Confira também
- [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)
