---
title: Interfaces de Avaliação de Expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736947"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de avaliação de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 A seguir estão as Interfaces [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de Avaliação de Expressão para o SDK de depuração.

## <a name="discussion"></a>Discussão
 Essas interfaces são usadas para avaliar expressões em uma pilha de chamadas durante o modo de pausa. Eles são implementados apenas para avaliadores de expressão em tempo de execução de linguagem comum (EE).

 Cada interface na tabela mostra o componente que pode implementá-lo a partir da seguinte lista:

- Motor de depuração (DE)

- Avaliador de Expressão (EE)

- Visual Studio (VS)

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa um pseudônimo numérico para uma variável.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa um alias numérico para uma variável e permite que um avaliador de expressão (EE) obtenha o domínio do aplicativo para o alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa um objeto de matriz.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa um objeto de matriz gerenciado e permite que um avaliador de expressão (EE) determine o índice base (limites inferiores) para a matriz.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa um fichário que liga símbolos de depuração a endereços reais na memória.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|O mesmo que a interface [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) mas fornece acesso a tipos, aliases e visualizadores personalizados.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa o avaliador de expressão.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa uma versão aprimorada de um avaliador de expressão (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa um avaliador de expressão (EE) com uma árvore de analisador aprimorada.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa uma função.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa uma função e aprimora a interface [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Habilita que um avaliador de expressão (EE) exiba uma mensagem na janela de saída do depurador.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa um objeto de código gerenciado.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface base que representa qualquer símbolo vinculado a um endereço de memória.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|O mesmo que a interface [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) mas fornece acesso a informações adicionais.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa uma expressão parsed pronta para ser avaliada.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa um ponteiro.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa um ponteiro em uma árvore de análise e estende a interface **IDebugPointerObject.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Fornece a capacidade de modificar o valor de um tipo através de um visualizador de tipo.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fornece acesso a visualizadores personalizados e visualizadores de tipos.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Fornece a capacidade de criar um objeto [IEEVisualizerService.](../../../extensibility/debugger/reference/ieevisualizerservice.md)|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa uma coleção de objetos [IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)|

## <a name="see-also"></a>Confira também
- [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Escrevendo um avaliador de expressão do CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
