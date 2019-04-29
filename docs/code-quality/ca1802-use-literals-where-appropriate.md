---
title: 'CA1802: Usar literais quando apropriado'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f4dbafb4c6f7ad590244842ac3def0e26f8a14fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797060"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Usar literais quando apropriado

|||
|-|-|
|NomeDoTipo|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um campo é declarado `static` e `readonly` (`Shared` e `ReadOnly` no Visual Basic) e é inicializada com um valor computável no tempo de compilação.

Por padrão, essa regra olha apenas para campos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

O valor de um `static readonly` campo é calculado em tempo de execução quando o construtor estático para o tipo declarativo é chamado. Se o `static readonly` campo é inicializado quando ela é declarada e um construtor estático não é declarado explicitamente, o compilador emite um construtor estático para inicializar o campo.

O valor de uma `const` campo é calculado em tempo de compilação e armazenado nos metadados, o que aumenta o desempenho de tempo de execução quando ele é comparado com um `static readonly` campo.

Como o valor atribuído ao campo de destino é computável no tempo de compilação, altere a declaração para um `const` campo para que o valor é calculado em tempo de compilação em vez de em tempo de execução.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, substitua os `static` e `readonly` modificadores com o `const` modificador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, ou desabilitar a regra, se o desempenho não for uma preocupação.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```
dotnet_code_quality.ca1802.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (desempenho). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo `UseReadOnly`, que viola a regra e um tipo, `UseConstant`, que satisfaz a regra.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]