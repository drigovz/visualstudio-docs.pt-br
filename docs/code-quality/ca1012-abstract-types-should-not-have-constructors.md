---
title: 'CA1012: Tipos abstratos não devem ter construtores'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef4bff83b1921b3cf15b25aaf225645379478f38
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236348"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Tipos abstratos não devem ter construtores

|||
|-|-|
|NomeDoTipo|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo é abstrato e tem um construtor.

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Construtores em tipos abstratos só podem ser chamados por tipos derivados. Como os construtores públicos criam instâncias de um tipo e você não pode criar instâncias de um tipo abstrato, um tipo abstrato que tem um construtor público é projetado incorretamente.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, torne o construtor protegido ou não declare o tipo como abstrato.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. O tipo abstrato tem um construtor público.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1012.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O trecho de código a seguir contém um tipo abstrato que viola essa regra.

[!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
[!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

O trecho de código a seguir corrige a violação anterior alterando a acessibilidade do construtor `public` de `protected`para.

[!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
[!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]