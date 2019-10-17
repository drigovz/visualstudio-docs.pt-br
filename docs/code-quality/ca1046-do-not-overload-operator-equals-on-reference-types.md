---
title: 'CA1046: não sobrecarregar igualdades de operador em tipos de referência'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31fd841117e3036cfb9068523914abd2d5f7797a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449171"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: não sobrecarregar igualdades de operador em tipos de referência

|||
|-|-|
|NomeDoTipo|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Categoria|Microsoft. Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo de referência pública pública ou aninhada sobrecarrega o operador de igualdade.

## <a name="rule-description"></a>Descrição da regra
Para tipos de referência, a implementação padrão do operador de igualdade está quase sempre correta. Por padrão, duas referências só serão iguais se apontarem para o mesmo objeto.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova a implementação do operador de igualdade.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra quando o tipo de referência se comporta como um tipo de valor interno. Se for significativo fazer adição ou subtração em instâncias do tipo, provavelmente será correto implementar o operador de igualdade e suprimir a violação.

## <a name="example"></a>Exemplo
O exemplo a seguir demonstra o comportamento padrão ao comparar duas referências.

[!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Exemplo

O aplicativo a seguir compara algumas referências.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Este exemplo gera a seguinte saída:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Regras relacionadas

[CA1013: sobrecarregar operador Equals ao sobrecarregar adicionar e subtrair](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators)
