---
title: 'CA2225: sobrecargas de operador têm nomes alternativos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 212abc1fa5e2debfaf7ca81d82c8d94e9ddb0879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658882"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: as sobrecargas do operador têm alternativas nomeadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Uma sobrecarga de operador foi detectada, e o método alternativo nomeado esperado não foi encontrado.

## <a name="rule-description"></a>Descrição da Regra
 A sobrecarga de operador permite o uso de símbolos para representar computações para um tipo. Por exemplo, um tipo que sobrecarrega o símbolo de mais (+) para adição normalmente teria um membro alternativo chamado ' Add '. O membro alternativo nomeado fornece acesso à mesma funcionalidade que o operador e é fornecido para desenvolvedores que programam em idiomas que não dão suporte a operadores sobrecarregados.

 Essa regra examina os operadores listados na tabela a seguir.

|C#|Visual Basic|C++|Nome alternativo|
|---------|------------------|-----------|--------------------|
|+ (binário)|+|+ (binário)|Adicionar|
|+=|+=|+=|Adicionar|
|&|And|&|BitwiseAnd|
|&=|E =|&=|BitwiseAnd|
|&#124;|Ou|&#124;|Operadora|
|&#124;=|Ou =|&#124;=|Operadora|
|--|N/A|--|Decremento|
|/|/|/|Divisão|
|/=|/=|/=|Divisão|
|==|=|==|Igual a|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Comparar|
|>=|>=|>=|Comparar|
|++|N/A|++|Incremento|
|<>|!=|Igual a|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Comparar|
|<=|<=|\<=|Comparar|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|Operador lógico|
|!|N/A|!|LogicalNot|
|%|Mod|%|Mod ou resto|
|%=|N/A|%=|Mod|
|* (binário)|*|*|Multiplicar|
|*=|N/A|*=|Multiplicar|
|~|não|~|OnesComplement|
|>>|>>|>>|RightShift|
=|N/A|>>=|RightShift|
|-(binário)|-(binário)|-(binário)|Subtração|
|-=|N/A|-=|Subtração|
|true|True|N/A|IsTrue (Propriedade)|
|- (unário)|N/A|-|Negar|
|+ (unário)|N/A|+|acrescido|
|false|IsFalse|False|IsTrue (Propriedade)|

 N/A = = não pode ser sobrecarregado no idioma selecionado.

 A regra também verifica os operadores de conversão implícitos e explícitos em um tipo (`SomeType`) verificando os métodos chamados `ToSomeType` e `FromSomeType`.

 No C#, quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também é implicitamente sobrecarregado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, implemente o método alternativo para o operador; Nomeie-o usando o nome alternativo recomendado.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não omita um aviso dessa regra se você estiver implementando uma biblioteca compartilhada. Os aplicativos podem ignorar um aviso dessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir define uma estrutura que viola essa regra. Para corrigir o exemplo, adicione um método público `Add(int x, int y)` à estrutura.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: não sobrecarregar operador Equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: os operadores devem ter sobrecargas simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: substituir Equals ao sobrecarregar o operador Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: sobrecarregar operador Equals ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
