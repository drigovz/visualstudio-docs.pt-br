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
ms.openlocfilehash: 7baf13eb9125b273ad8fb1265a65eb7b053238a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779118"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implementar construtores de exceção padrão

|||
|-|-|
|NomeDoTipo|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Estende um tipo <xref:System.Exception?displayProperty=fullName> , mas não declara todos os construtores.

## <a name="rule-description"></a>Descrição da regra

Tipos de exceção devem implementar os três construtores a seguir:

- NewException() pública

- NewException(string) pública

- público NewException exceção (string)

Além disso, se você estiver executando a análise de código estático FxCop herdado como em vez de [analisadores FxCop baseada em Roslyn](../code-quality/roslyn-analyzers-overview.md), a ausência de um quarto construtor também gera uma violação:

- NewException protegida ou privada (SerializationInfo, StreamingContext)

Deixar de fornecer o conjunto completo de construtores pode dificultar o tratamento correto das exceções. Por exemplo, o construtor que tem a assinatura `NewException(string, Exception)` é usado para criar as exceções causadas por outras exceções. Sem esse construtor, você não pode criar e lançar uma instância de sua exceção personalizada que contém uma exceção interna (aninhada), que é o que o código gerenciado deve fazer nessa situação.

Os construtores de três exceção primeiros são públicos por convenção. O quarto construtor é protegido em classes não seladas e privado em classes sealed. Para obter mais informações, consulte [CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicionar os construtores ausentes para a exceção e certifique-se de que eles têm a acessibilidade correta.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, quando a violação é causada pelo uso de um nível de acesso diferentes para os construtores públicos. Além disso, ele é okey suprimir o aviso para o `NewException(SerializationInfo, StreamingContext)` construtor se você estiver criando uma biblioteca de classe portátil (PCL).

## <a name="example"></a>Exemplo

O exemplo a seguir contém um tipo de exceção que viola essa regra e um tipo de exceção que é implementado corretamente.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Consulte também

[CA2229: implementar construtores de serialização](../code-quality/ca2229-implement-serialization-constructors.md)