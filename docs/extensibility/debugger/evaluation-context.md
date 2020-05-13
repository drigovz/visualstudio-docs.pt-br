---
title: Contexto de Avaliação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738806"
---
# <a name="evaluation-context"></a>Contexto de avaliação
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE), três argumentos que são passados para [AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinam o contexto para encontrar e avaliar símbolos, conforme mostrado na tabela a seguir.

## <a name="arguments"></a>Argumentos

|Argumento|Descrição|
|--------------|-----------------|
|`pSymbolProvider`|Uma interface [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) que especifica o manipulador de símbolos (SH) a ser usado para identificar o símbolo.|
|`pAddress`|Uma interface [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) que especifica o ponto de execução atual. Esta interface encontra o método que contém o código que está sendo executado.|
|`pBinder`|Uma interface [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) que encontra o valor e o tipo de um símbolo dado seu nome.|

 `IDebugParsedExpression::EvaluateSync`retorna uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) representando o valor resultante e seu tipo.

## <a name="see-also"></a>Confira também
- [Principais interfaces avaliadoras de expressão](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Exibindo locais](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
