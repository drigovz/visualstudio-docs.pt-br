---
title: Interfaces do avaliador de expressão da chave | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72407753960b38fc604d069d4e78b91a02eb737b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63411196"
---
# <a name="key-expression-evaluator-interfaces"></a>Interfaces do avaliador de expressão de chave
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ao escrever um avaliador de expressão (EE), junto com o contexto de avaliação, você deve estar familiarizado com as seguintes interfaces.

## <a name="interface-descriptions"></a>Descrições da interface

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     Tem um único método, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), que obtém uma estrutura de dados que representa o ponto atual de execução. Essa estrutura de dados é um dos três argumentos que o mecanismo de depuração (DES) passa para o [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) método para avaliar uma expressão. Normalmente, essa interface é implementada pelo provedor de símbolo.

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     Tem o [associar](../../extensibility/debugger/reference/idebugbinder-bind.md) método, que obtém a área de memória que contém o valor atual de um símbolo. Com o método recipiente, representado por um [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto e o símbolo em si, representado por um [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto, `IDebugBinder::Bind` retorna o valor do símbolo. `IDebugBinder` costuma ser implementada por DE.

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     Representa um tipo de dados simples. Para tipos mais complexos, como matrizes e métodos, use o derivada [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) e [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaces, respectivamente. [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) é outra interface derivada importante que representa os símbolos que contém outros símbolos, como métodos ou classes. O `IDebugField` interface (e seus derivados) normalmente são implementados pelo provedor de símbolo.

     Uma `IDebugField` objeto pode ser usada para localizar o nome e tipo de um símbolo e, junto com um [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) de objeto, pode ser usado para localizar seu valor.

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     Representa os bits reais do valor de tempo de execução de um símbolo. [Associar](../../extensibility/debugger/reference/idebugbinder-bind.md) usa um [IDebugField](../../extensibility/debugger/reference/idebugfield.md) object, que representa um símbolo e retorna um [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto. O [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) método retorna o valor do símbolo em um buffer de memória. Normalmente, a DE implementa essa interface para representar o valor de uma propriedade na memória.

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     Essa interface representa o avaliador de expressão. O método principal é [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), que retorna um [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface.

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     Essa interface representa uma expressão analisada pronta para ser avaliada. O método principal é [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) que retorna um IDebugProperty2 que representa o valor e o tipo da expressão.

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     Essa interface representa um valor e seu tipo e é o resultado de uma avaliação de expressão.

## <a name="see-also"></a>Consulte também
- [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md)