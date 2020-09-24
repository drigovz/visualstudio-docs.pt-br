---
title: Exemplo de implementação de avaliação de expressão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7a19247b296d7e00a15051e75dd53536133c426
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147244"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Exemplo de implementação de avaliação de expressão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Para uma expressão de janela de **inspeção** , o Visual Studio chama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para produzir um objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) . `IDebugExpressionContext2::ParseText` Cria uma instância de um avaliador de expressão (EE) e chama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obter um objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
 Essa implementação do `IDebugExpressionEvaluator::Parse` executa as seguintes tarefas:  
  
1. [Somente C++] Analisa a expressão para procurar erros.  
  
2. Cria uma instância de uma classe (chamada `CParsedExpression` neste exemplo) que implementa a `IDebugParsedExpression` interface e armazena na classe a expressão a ser analisada.  
  
3. Retorna a `IDebugParsedExpression` interface do `CParsedExpression` objeto.  
  
> [!NOTE]
> Nos exemplos a seguir e no exemplo MyCEE, o avaliador de expressão não separa a análise da avaliação.  
  
## <a name="managed-code"></a>Código gerenciado  
 Esta é uma implementação do `IDebugExpressionEvaluator::Parse` em código gerenciado. Observe que essa versão do método adia a análise para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , pois o código para análise também é avaliado ao mesmo tempo (consulte [avaliando uma expressão Watch](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Código não gerenciado  
 Esta é uma implementação do `IDebugExpressionEvaluator::Parse` em código não gerenciado. Esse método chama uma função auxiliar, `Parse` , para analisar a expressão e verificar se há erros, mas esse método ignora o valor resultante. A avaliação formal é adiada para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) em que a expressão é analisada enquanto é avaliada (consulte [avaliando uma expressão de inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)).  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Avaliando uma expressão de janela de inspeção](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [Avaliando uma expressão de inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)
