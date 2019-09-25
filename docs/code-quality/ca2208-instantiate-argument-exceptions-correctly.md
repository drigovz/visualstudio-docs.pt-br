---
title: 'CA2208: Criar instância de exceções de argumento corretamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231639"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Criar instância de exceções de argumento corretamente

|||
|-|-|
|NomeDoTipo|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

As possíveis causas incluem as seguintes situações:

- É feita uma chamada para o construtor padrão (sem parâmetros) de um tipo de exceção que é, ou deriva de, <xref:System.ArgumentException>.

- Um argumento de cadeia de caracteres incorreto é passado para um construtor com parâmetros de um tipo de exceção que é, <xref:System.ArgumentException>ou deriva de,.

## <a name="rule-description"></a>Descrição da regra

Em vez de chamar o construtor padrão, chame uma das sobrecargas do construtor que permite que uma mensagem de exceção mais significativa seja fornecida. A mensagem de exceção deve ter como alvo o desenvolvedor e explicar claramente a condição de erro e como corrigir ou evitar a exceção.

As assinaturas de um e dois construtores de cadeia de caracteres <xref:System.ArgumentException> de e seus tipos derivados não são consistentes em relação à `message` posição `paramName` e aos parâmetros. Verifique se esses construtores são chamados com os argumentos de cadeia de caracteres corretos. As assinaturas são as seguintes:

- <xref:System.ArgumentException>(cadeia `message`de caracteres)
- <xref:System.ArgumentException>(cadeia `message`de caracteres `paramName`, Cadeia de caracteres)
- <xref:System.ArgumentNullException>(cadeia `paramName`de caracteres)
- <xref:System.ArgumentNullException>(cadeia `paramName`de caracteres `message`, Cadeia de caracteres)
- <xref:System.ArgumentOutOfRangeException>(cadeia `paramName`de caracteres)
- <xref:System.ArgumentOutOfRangeException>(cadeia `paramName`de caracteres `message`, Cadeia de caracteres)
- <xref:System.DuplicateWaitObjectException>(cadeia `parameterName`de caracteres)
- <xref:System.DuplicateWaitObjectException>(cadeia `parameterName`de caracteres `message`, Cadeia de caracteres)

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, chame um construtor que receba uma mensagem, um nome de parâmetro ou ambos, e verifique se os argumentos são adequados para o tipo de <xref:System.ArgumentException> chamada.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra somente se um construtor com parâmetros for chamado com os argumentos de cadeia de caracteres corretos.

## <a name="example"></a>Exemplo

O código a seguir mostra um construtor que instancia incorretamente uma instância do <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

O código a seguir corrige a violação anterior alternando os argumentos do construtor.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1507: Usar nameof no lugar da cadeia de caracteres](ca1507.md)