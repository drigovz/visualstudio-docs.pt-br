---
title: Estratégia de Implementação avaliadora de expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738676"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estratégia de implementação do avaliador de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Uma abordagem para criar rapidamente um avaliador de expressão (EE) é primeiro implementar o código mínimo necessário para exibir variáveis locais na janela **Locais.** É útil perceber que cada linha na janela **Locals** exibe o nome, o tipo e o valor de uma variável local, e que todas as três são representadas por um objeto [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) O nome, o tipo e o valor de `IDebugProperty2` uma variável local são obtidos a partir de um objeto, chamando seu método [GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Para obter mais informações sobre como exibir variáveis locais na janela **Locals,** consulte [Exibindo locais](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussão
 Uma possível seqüência de implementação começa com a implementação do [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Os métodos [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devem ser implementados para exibir os locais. Chamar `IDebugExpressionEvaluator::GetMethodProperty` retorna `IDebugProperty2` um objeto que representa um método: ou seja, um objeto [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Os métodos em si não são exibidos na janela **Locais.**

 O método [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) deve ser implementado em seguida. O mecanismo de depuração (DE) chama esse método para obter `IDebugProperty2::EnumChildren` `guidFilter` uma `guidFilterLocalsPlusArgs`lista de variáveis e argumentos locais, passando um argumento de . `IDebugProperty2::EnumChildren`chama [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals,](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)combinando os resultados em uma única enumeração. Consulte Exibir locais para obter mais [detalhes.](../../extensibility/debugger/displaying-locals.md)

## <a name="see-also"></a>Confira também
- [Implementar um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Mostrar locais](../../extensibility/debugger/displaying-locals.md)
