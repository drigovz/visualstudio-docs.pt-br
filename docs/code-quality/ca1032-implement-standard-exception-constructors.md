---
title: 'CA1032: Implementar construtores de exceção padrão'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad062154b8213d021c8c265aaf287d3a9335d0e4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922875"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar construtores de exceção padrão

|||
|-|-|
|NomeDoTipo|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Categoria|Microsoft.Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo se <xref:System.Exception?displayProperty=fullName> estende, mas não declara todos os construtores necessários.

## <a name="rule-description"></a>Descrição da regra

Os tipos de exceção devem implementar os três construtores a seguir:

- NewException público ()

- NewException público (cadeia de caracteres)

- NewException público (cadeia de caracteres, exceção)

Além disso, se você estiver executando uma análise de código estático do FxCop herdado em oposição a [analisadores de FxCop baseados em Roslyn](../code-quality/roslyn-analyzers-overview.md), a ausência de um quarto construtor também gerará uma violação:

- NewException protegidos ou privados (SerializationInfo, StreamingContext)

Deixar de fornecer o conjunto completo de construtores pode dificultar o tratamento correto das exceções. Por exemplo, o construtor que tem a assinatura `NewException(string, Exception)` é usado para criar exceções que são causadas por outras exceções. Sem esse construtor, você não pode criar e lançar uma instância de sua exceção personalizada que contém uma exceção interna (aninhada), que é o código gerenciado que deve ser feito nessa situação.

Os três primeiros construtores de exceção são públicos por convenção. O quarto construtor é protegido em classes sem lacre e privado em classes lacradas. Para obter mais informações, [consulte CA2229: Implementar construtores](../code-quality/ca2229-implement-serialization-constructors.md)de serialização.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione os construtores ausentes à exceção e verifique se eles têm a acessibilidade correta.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra quando a violação é causada pelo uso de um nível de acesso diferente para os construtores públicos. Além disso, não há problema em suprimir o aviso `NewException(SerializationInfo, StreamingContext)` para o Construtor se você estiver criando uma PCL (biblioteca de classes portátil).

## <a name="example"></a>Exemplo

O exemplo a seguir contém um tipo de exceção que viola essa regra e um tipo de exceção que é implementado corretamente.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Consulte também

[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)