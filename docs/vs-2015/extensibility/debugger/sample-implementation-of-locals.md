---
title: Exemplo de implementação de locais | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e943fd7ba27fe21029bab4d818803186147476e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704883"
---
# <a name="sample-implementation-of-locals"></a>Implementação de exemplo de locais
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Aqui está uma visão geral de como o Visual Studio obtém os locais para um método do avaliador de expressão (EE):  
  
1. O Visual Studio chama o mecanismo de depuração [Getdebugproperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obter um objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa todas as propriedades do quadro de pilha, incluindo os locais.  
  
2. `IDebugStackFrame2::GetDebugProperty` chama [Getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obter um objeto que descreve o método no qual o ponto de interrupção ocorreu. O DE fornece um provedor de símbolos ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), um endereço ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e um associador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3. `IDebugExpressionEvaluator::GetMethodProperty` chama [Getcontainerfield](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) com o `IDebugAddress` objeto fornecido para obter um [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa o método que contém o endereço especificado.  
  
4. A `IDebugContainerField` interface é consultada para a interface [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) . É essa interface que dá acesso aos locais do método.  
  
5. `IDebugExpressionEvaluator::GetMethodProperty` Cria uma instância de uma classe (chamada `CFieldProperty` no exemplo) que implementa a `IDebugProperty2` interface para representar os locais do método. O `IDebugMethodField` objeto é colocado nesse `CFieldProperty` objeto junto com os `IDebugSymbolProvider` `IDebugAddress` `IDebugBinder` objetos e.  
  
6. Quando o `CFieldProperty` objeto é inicializado, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) é chamado no `IDebugMethodField` objeto para obter uma estrutura de [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) que contém todas as informações de exibição sobre o próprio método.  
  
7. `IDebugExpressionEvaluator::GetMethodProperty` Retorna o `CFieldProperty` objeto como um `IDebugProperty2` objeto.  
  
8. O Visual Studio chama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) no `IDebugProperty2` objeto retornado com o filtro `guidFilterLocalsPlusArgs` . Isso retorna um objeto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contendo os locais do método. Essa enumeração é preenchida por chamadas para [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. O Visual Studio chama [Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obter uma estrutura de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) para cada local. Essa estrutura contém um ponteiro para uma `IDebugProperty2` interface para um local.  
  
10. O Visual Studio chama [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local para obter o nome, o valor e o tipo do local. Essas são as informações que são exibidas na janela **locais** .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementar GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Descreve uma implementação de [Getmethodproperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerar Locals](../../extensibility/debugger/enumerating-locals.md)  
 Descreve como o mecanismo de depuração (DE) faz uma chamada para enumerar variáveis locais ou argumentos.  
  
 [Obter as propriedades do Local](../../extensibility/debugger/getting-local-properties.md)  
 Descreve como o DE faz uma chamada para obter o nome, o tipo e o valor de um ou mais locais.  
  
 [Obter valores de Local](../../extensibility/debugger/getting-local-values.md)  
 Discute como obter o valor do local, que exige os serviços de um objeto de associador fornecido pelo contexto de avaliação.  
  
 [Avaliar Locals](../../extensibility/debugger/evaluating-locals.md)  
 Explica como os locais são avaliados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Contexto da avaliação](../../extensibility/debugger/evaluation-context.md)  
 Fornece os argumentos que são passados quando o DE chama o avaliador de expressão (EE).  
  
 [Exemplo de MyCEE](https://msdn.microsoft.com/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Demonstra uma abordagem de implementação para criar um avaliador de expressão para o idioma MyC.  
  
## <a name="see-also"></a>Consulte Também  
 [Exibir Locals](../../extensibility/debugger/displaying-locals.md)
