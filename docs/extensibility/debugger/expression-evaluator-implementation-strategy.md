---
title: Estratégia de implementação do avaliador de expressão | Microsoft Docs
description: Saiba mais sobre uma estratégia para criar um avaliador de expressão, primeiro implementando o código para exibir variáveis locais na janela locais.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7527c361a889d5aa1f19ec7a211f8aeb8dcbd15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921389"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estratégia de implementação do avaliador de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Uma abordagem para criar rapidamente um avaliador de expressão (EE) é primeiro implementar o código mínimo necessário para exibir variáveis locais na janela **locais** . É útil perceber que cada linha na janela **locais** exibe o nome, o tipo e o valor de uma variável local, e que todas as três são representadas por um objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . O nome, o tipo e o valor de uma variável local são obtidos de um `IDebugProperty2` objeto chamando seu método [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Para obter mais informações sobre como exibir variáveis locais na janela **locais** , consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md).

## <a name="discussion"></a>Discussão
 Uma sequência de implementação possível começa com a implementação de [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Os métodos [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) devem ser implementados para exibir locais. Chamar `IDebugExpressionEvaluator::GetMethodProperty` retorna um `IDebugProperty2` objeto que representa um método: ou seja, um objeto [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . Os próprios métodos não são exibidos na janela **locais** .

 O método [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) deve ser implementado em seguida. O mecanismo de depuração (DE) chama esse método para obter uma lista de variáveis e argumentos locais, passando `IDebugProperty2::EnumChildren` um `guidFilter` argumento de `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` chama [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando os resultados em uma única enumeração. Consulte [Exibir locais](../../extensibility/debugger/displaying-locals.md) para obter mais detalhes.

## <a name="see-also"></a>Confira também
- [Implementar um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Exibir locais](../../extensibility/debugger/displaying-locals.md)
