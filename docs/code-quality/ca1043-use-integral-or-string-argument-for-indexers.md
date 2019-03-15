---
title: 'CA1043: Usar argumento integral ou de cadeia de caracteres para indexadores'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3d47b39208fce297fd058d6976b9fa7d7593cb9a
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867145"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Usar argumento integral ou de cadeia de caracteres para indexadores

|||
|-|-|
|NomeDoTipo|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo contém um indexador que usa um tipo de índice diferente de <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, ou <xref:System.String?displayProperty=fullName>.

Por padrão, essa regra olha apenas tipos públicos e protegidos, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Indexadores, ou seja, propriedades indexadas, devem usar tipos de inteiro ou cadeia de caracteres para o índice. Esses tipos são normalmente usados para indexar estruturas de dados e aumentam a usabilidade da biblioteca. Usar o <xref:System.Object> tipo deve ser restrito a esses casos em que o tipo de inteiro ou cadeia de caracteres específico não pode ser especificado em tempo de design. Se o projeto requer outros tipos para o índice, reconsidere se o tipo representa um armazenamento de dados lógicos. Se ele não representa um repositório de dados lógicos, use um método.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, alterar o índice para um tipo de inteiro ou cadeia de caracteres ou usar um método em vez do indexador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprima um aviso nessa regra somente após considerar cuidadosamente a necessidade do indexador não padrão.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```
dotnet_code_quality.ca1043.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um indexador que usa um <xref:System.Int32> índice.

[!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
[!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
[!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1023: Indexadores não devem ser multidimensionais](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)
- [CA1024: Usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)