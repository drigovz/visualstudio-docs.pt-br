---
title: 'CA1036: Substituir métodos em tipos comparáveis'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d08644ede6b9b28496cff585624ea37858afd49
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842298"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Substituir métodos em tipos comparáveis

|||
|-|-|
|NomeDoTipo|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um tipo implementa o <xref:System.IComparable?displayProperty=fullName> da interface e não substitui <xref:System.Object.Equals%2A?displayProperty=fullName> ou sobrecarrega o operador de idioma específico para igualdade, desigualdade, menor-que ou maior-que. A regra não relata uma violação se o tipo herdar apenas uma implementação da interface.

Por padrão, essa regra olha apenas tipos públicos e protegidos, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Tipos que definem uma ordem de classificação personalizada é implementar o <xref:System.IComparable> interface. O <xref:System.IComparable.CompareTo%2A> método retorna um valor inteiro que indica a ordem de classificação correta para que duas instâncias do tipo. Essa regra identifica os tipos que definir uma ordem de classificação. Definir uma ordem de classificação implica que o significado comum de igualdade, desigualdade, menor-que e maior-que não se aplicam. Quando você fornece uma implementação de <xref:System.IComparable>, você geralmente deve também substituir <xref:System.Object.Equals%2A> para que ele retorna valores que são consistentes com <xref:System.IComparable.CompareTo%2A>. Se você substituir <xref:System.Object.Equals%2A> e está codificando em uma linguagem que dá suporte a sobrecargas de operador, você também deve fornecer os operadores que são consistentes com <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, substituir <xref:System.Object.Equals%2A>. Se sua linguagem de programação dá suporte à sobrecarga de operador, fornece os seguintes operadores:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

No c#, os tokens que são usados para representar esses operadores são:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso de regra CA1036 quando a violação é causada por falta de operadores e sua linguagem de programação não oferece suporte a sobrecarga de operador, como é o caso com o Visual Basic. Se você determinar que a implementar os operadores não faz sentido no contexto de seu aplicativo, também é seguro suprimir um aviso nessa regra quando ela é acionada em operadores de igualdade diferentes op_Equality. No entanto, você sempre deve substituir op_Equality e o operador = = se você substituir <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="examples"></a>Exemplos

O código a seguir contém um tipo que implementa corretamente <xref:System.IComparable>. Comentários de código identificam os métodos que atendem a várias regras que estão relacionadas ao <xref:System.Object.Equals%2A> e o <xref:System.IComparable> interface.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

O código de aplicativo a seguir testa o comportamento do <xref:System.IComparable> implementação mostrado anteriormente.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators)