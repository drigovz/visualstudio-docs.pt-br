---
title: 'CA1052: Tipos de suporte estático devem ser selados'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 346a7f4cc7c7a8e6f579f94c6294ce9577fa01c7
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842085"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Tipos de suporte estático devem ser selados

|||
|-|-|
|NomeDoTipo|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo não abstrato contém apenas membros estáticos e não é declarado com o [lacrado](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificador.

Por padrão, essa regra olha apenas tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

CA1052 regra pressupõe que um tipo que contém apenas membros estáticos não foi projetado para ser herdadas, pois o tipo não fornece nenhuma funcionalidade que pode ser substituída em um tipo derivado. Um tipo que não se destina a ser herdada que deve ser marcado com o `sealed` ou `NotInheritable` modificador para proibir o uso como um tipo base. Essa regra não é disparado para classes abstratas.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, marque o tipo como `sealed` ou `NotInheritable`. Se você estiver direcionando o .NET Framework 2.0 ou posterior, uma abordagem melhor é marcar o tipo como `static` ou `Shared`. Dessa forma, você não precisa declarar um construtor particular para impedir que a classe que está sendo criado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprima um aviso nessa regra somente se o tipo foi projetado para ser herdada. A ausência do `sealed` ou `NotInheritable` modificador sugere que o tipo é útil como um tipo base.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemplo de uma violação

O exemplo a seguir mostra um tipo que viola a regra:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>Corrigir com o modificador estático

O exemplo a seguir mostra como corrigir uma violação dessa regra, marcando o tipo com o `static` modificador em C#:

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1053: Tipos de espaços reservados estáticos não devem ter construtores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)