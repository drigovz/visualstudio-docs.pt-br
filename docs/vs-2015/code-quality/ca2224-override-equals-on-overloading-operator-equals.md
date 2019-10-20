---
title: 'CA2224: substituir Equals no operador de sobrecarga Equals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d35052bb2a1efb1a466ffc67c95c83e5b3a76533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671887"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: substituir igualdades em igualdades de operador de sobrecarga
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo público implementa o operador de igualdade, mas não substitui <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 O operador de igualdade deve ser uma maneira sintaticamente conveniente de acessar a funcionalidade do método <xref:System.Object.Equals%2A>. Se você implementar o operador de igualdade, sua lógica deverá ser idêntica à de <xref:System.Object.Equals%2A>.

 O C# compilador emitirá um aviso se o seu código violar essa regra.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, você deve remover a implementação do operador de igualdade ou substituir <xref:System.Object.Equals%2A> e fazer com que os dois métodos retornem os mesmos valores. Se o operador de igualdade não apresentar comportamento inconsistente, você poderá corrigir a violação fornecendo uma implementação de <xref:System.Object.Equals%2A> que chama o método <xref:System.Object.Equals%2A> na classe base.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se o operador de igualdade retornar o mesmo valor que a implementação herdada de <xref:System.Object.Equals%2A>. A seção de exemplo inclui um tipo que pode suprimir com segurança um aviso dessa regra.

## <a name="examples-of-inconsistent-equality-definitions"></a>Exemplos de definições de igualdade inconsistentes

### <a name="description"></a>Descrição
 O exemplo a seguir mostra um tipo com definições de igualdade inconsistentes. `BadPoint` altera o significado de igualdade fornecendo uma implementação personalizada do operador de igualdade, mas não substitui <xref:System.Object.Equals%2A> para que ele se comporta de forma idêntica.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Exemplo
 O código a seguir testa o comportamento de `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **a = ([0] 1, 1) e b = ([1] 2, 2) são iguais? Não** 
**a = b? Nenhuma** 
**a1 e a é igual? Sim** 
**a1 = = a? Sim** 
**b e bcopy são iguais? Não** 
**b = = bcopy? Sim**
## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que, tecnicamente, viola essa regra, mas não se comporta de maneira inconsistente.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Exemplo
 O código a seguir testa o comportamento de `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Este exemplo gerencia a seguinte saída.

 **a = (1, 1) e b = (2, 2) são iguais? Não** 
**a = b? Nenhuma** 
**a1 e a é igual? Sim** 
**a1 = = a? Sim** 
**b e bcopy são iguais? Sim** 
**b = = bcopy? Sim**
## <a name="class-example"></a>Exemplo de classe

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma classe (tipo de referência) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação substituindo <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Exemplo de estrutura

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma estrutura (tipo de valor) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir corrige a violação substituindo <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: as sobrecargas do operador têm alternativos nomeados](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
