---
title: 'CA1815: substituir Equals e Operator Equals em tipos Value | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb9574eb6e9f907d4b1fcc74f50fca0e7db85253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668400"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: substituir igualdades e igualdades de operador em tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Categoria|Microsoft. performance|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo de valor público não substitui <xref:System.Object.Equals%2A?displayProperty=fullName> ou não implementa o operador de igualdade (= =). Essa regra não verifica enumerações.

## <a name="rule-description"></a>Descrição da Regra
 Para tipos de valor, a implementação herdada de <xref:System.Object.Equals%2A> usa a biblioteca de reflexão e compara o conteúdo de todos os campos. Reflection é computacionalmente cara, e pode ser desnecessário comparar a igualdade de cada campo. Se você espera que os usuários comparem ou classifiquem instâncias, ou use-as como chaves de tabela de hash, seu tipo de valor deve implementar <xref:System.Object.Equals%2A>. Se a linguagem de programação der suporte à sobrecarga de operador, também é necessário fornecer uma implementação dos operadores de igualdade e desigualdade.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, forneça uma implementação de <xref:System.Object.Equals%2A>. Se puder, implemente o operador de igualdade.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se as instâncias do tipo de valor não forem comparadas entre si.

## <a name="example-of-a-violation"></a>Exemplo de uma violação

### <a name="description"></a>Descrição
 O exemplo a seguir mostra uma estrutura (tipo de valor) que viola essa regra.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Exemplo de como corrigir

### <a name="description"></a>Descrição
 O exemplo a seguir corrige a violação anterior, substituindo <xref:System.ValueType.Equals%2A?displayProperty=fullName> e implementando os operadores de igualdade (= =,! =).

### <a name="code"></a>Código
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Object.Equals%2A?displayProperty=fullName>
