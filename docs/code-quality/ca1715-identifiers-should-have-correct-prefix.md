---
title: 'CA1715: Identificadores devem ter um prefixo correto'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ca9c4681cc19917ef965a4c8577e9559d71dd4be
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841960"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Identificadores devem ter um prefixo correto

|||
|-|-|
|NomeDoTipo|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebrando - quando disparado em interfaces.<br /><br /> Sem quebra - quando gerado em parâmetros de tipo genérico.|

## <a name="cause"></a>Causa

O nome de uma interface não começar com letras maiusculas 'I'.

- ou -

O nome de um [parâmetro de tipo genérico](/dotnet/csharp/programming-guide/generics/generic-type-parameters) em um tipo ou método não começa com uma letra maiuscula ' t '.

Por padrão, essa regra olha apenas interfaces visíveis externamente, tipos e métodos, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Por convenção, os nomes de determinados elementos de programação começar com um prefixo específico.

Nomes de interface devem começar com uma letra maiuscula 'I' seguido de outra letra maiuscula. Esta regra relata violações para nomes de interface, como 'MyInterface' e 'IsolatedInterface'.

Nomes de parâmetro de tipo genérico devem começar com uma letra maiuscula ' t ' e, opcionalmente, pode ser seguido por outra letra maiuscula. Esta regra relata violações para nomes de parâmetro de tipo genérico, como "V" e 'Type'.

Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes do seu código esta regra analisa. Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

### <a name="single-character-type-parameters"></a>Parâmetros de tipo de caractere único

Você pode configurar se deseja ou não excluir parâmetros de tipo de caractere único da regra. Por exemplo, para especificar que essa regra *não deve* analisar parâmetros de tipo de caractere único, adicione um dos seguintes pares chave-valor para um arquivo. editorconfig em seu projeto:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA1715.exclude_single_letter_type_parameters = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.allow_single_letter_type_parameters = true
```

> [!NOTE]
> Essa regra nunca é acionado para um parâmetro de tipo nomeado `T`, por exemplo, `Collection<T>`.

### <a name="api-surface"></a>Superfície de API

Você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1715.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (nomenclatura).

## <a name="how-to-fix-violations"></a>Como corrigir violações

Renomear o identificador para que ele será prefixado corretamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="interface-naming-example"></a>Exemplo de nomeação de interface

O trecho de código a seguir mostra uma interface nomeada incorretamente:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

O trecho de código a seguir corrige a violação anterior prefixando a interface com 'I':

[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="type-parameter-naming-example"></a>Exemplo de nomenclatura de parâmetro de tipo

O trecho de código a seguir mostra um parâmetro de tipo genérico nomeado incorretamente:

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

O trecho de código a seguir corrige a violação anterior, prefixando o parâmetro de tipo genérico com T' ':

[!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
[!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
[!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1722: Identificadores não devem ter prefixo incorreto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)