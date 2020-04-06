---
title: Implementando um Avaliador de Expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738547"
---
# <a name="implement-an-expression-evaluator"></a>Implementar um avaliador de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Avaliar uma expressão é uma interação complexa entre o mecanismo de depuração (DE), o provedor de símbolos (SP), o objeto de aglutinante e o avaliador de expressão (EE). Esses quatro componentes são conectados por interfaces que são implementadas por um componente e consumidas por outro.

 O EE toma uma expressão do DE na forma de uma seqüência e analisa ou avalia-a. O EE executa as seguintes interfaces, que são consumidas pelo DE:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  O EE chama o objeto de encadernação, fornecido pelo DE, para obter o valor de símbolos e objetos. O EE consome as seguintes interfaces, que são implementadas pelo DE:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  O EE executa [o IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2`fornece o mecanismo para descrever o resultado de uma avaliação de expressão, como uma variável local, um primitivo ou um objeto para o Visual Studio, que exibe as informações apropriadas na janela **Locals**, **Watch**ou **Immediate.**

  O SP é entregue ao EE pelo DE quando pede informações. A SP executa interfaces que descrevem endereços e campos, como as seguintes interfaces e seus derivados:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  O EE consome todas essas interfaces.

## <a name="in-this-section"></a>Nesta seção
 [Estratégia de implementação do avaliador de expressão](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) Define um processo de três etapas para a estratégia de implementação do avaliador de expressão (EE).

## <a name="see-also"></a>Confira também
- [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
