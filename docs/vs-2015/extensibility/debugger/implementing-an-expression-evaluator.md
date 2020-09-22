---
title: Implementando um avaliador de expressão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838346"
---
# <a name="implementing-an-expression-evaluator"></a>Implementando um avaliador de expressão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Avaliar uma expressão é uma interatividade complexa entre o mecanismo DE depuração (DE), o provedor de símbolos (SP), o objeto de fichário e o avaliador de expressão (EE) em si. Esses quatro componentes são conectados por interfaces que são implementadas por um componente e consumidas por outro.  
  
 O EE usa uma expressão de de na forma de uma cadeia de caracteres e a analisa ou avalia. O EE implementa as seguintes interfaces, que são consumidas pelo:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  O EE chama o objeto Binder, fornecido pelo DE, para obter o valor de símbolos e objetos. O EE consome as seguintes interfaces, que são implementadas pelo DE:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  O EE implementa [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fornece o mecanismo para descrever o resultado de uma avaliação de expressão, como uma variável local, um primitivo ou um objeto, para o Visual Studio, que exibe as informações apropriadas na janela **locais**, **inspecionar**ou **imediato** .  
  
  O SP é fornecido ao EE pelo DE quando ele solicita informações. O SP implementa interfaces que descrevem endereços e campos, como as seguintes interfaces e seus derivados:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  O EE consome todas essas interfaces.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estratégia de implementação do avaliador de expressão](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define um processo de três etapas para a estratégia de implementação do avaliador de expressão (EE).  
  
## <a name="see-also"></a>Consulte Também  
 [Escrevendo um avaliador de expressão do CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
