---
title: Alterando o valor de um local | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739142"
---
# <a name="change-the-value-of-a-local"></a>Alterar o valor de um local
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando um novo valor é digitado no campo de valor da janela **Locais,** o pacote de depuração passa a seqüência, conforme digitado, para o avaliador de expressão (EE). O EE avalia essa string, que pode conter um valor simples ou uma expressão, e armazena o valor resultante no local associado.

 Esta é uma visão geral do processo de alteração do valor de um local:

1. Depois que o usuário insere o novo valor, o Visual Studio chama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) no objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) associado ao local.

2. `IDebugProperty2::SetValueAsString` realiza as seguintes tarefas:

   1. Avalia a corda para produzir um valor.

   2. Vincula o objeto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) associado para obter um objeto [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Converte o valor em uma série de bytes.

   4. Chama [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar os bytes do valor na memória para que o programa que está sendo depurado possa acessá-los.

3. O Visual Studio atualiza a exibição **local** (veja Exibindo locais para obter [detalhes).](../../extensibility/debugger/displaying-locals.md)

   Este procedimento também é usado para alterar o valor de uma `IDebugProperty2` variável na janela **do relógio,** exceto que é o objeto associado ao valor do local que é usado em vez do `IDebugProperty2` objeto associado ao próprio local.

## <a name="in-this-section"></a>Nesta seção
 [Implementação amostral de valores de mudança](../../extensibility/debugger/sample-implementation-of-changing-values.md) Usa a amostra MyCEE para passar pelo processo de mudança de valores.

## <a name="see-also"></a>Confira também
- [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Exibindo locais](../../extensibility/debugger/displaying-locals.md)
