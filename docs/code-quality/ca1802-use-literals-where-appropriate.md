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
ms.openlocfilehash: 435eb5a9fd7e41a69c873df4c728e42551734a37
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253359"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Usar literais quando apropriado

|||
|-|-|
|NomeDoTipo|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um campo é declarado `static` e `readonly` (`Shared` e `ReadOnly` em Visual Basic) e é inicializado com um valor que é computáveis no momento da compilação.

Por padrão, essa regra só examina os campos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

O valor de um `static readonly` campo é calculado em tempo de execução quando o construtor estático para o tipo declarativo é chamado. Se o `static readonly` campo for inicializado quando for declarado e um construtor estático não for declarado explicitamente, o compilador emitirá um construtor estático para inicializar o campo.

O valor de um `const` campo é calculado no momento da compilação e armazenado nos metadados, o que aumenta o desempenho em tempo de execução quando ele é comparado `static readonly` a um campo.

Como o valor atribuído ao campo de destino é computáveis em tempo de compilação, altere a declaração para `const` um campo para que o valor seja computado em tempo de compilação em vez de em tempo de execução.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, substitua os `static` modificadores e `readonly` pelo `const` modificador.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra ou desabilitar a regra, se o desempenho não for preocupante.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1802.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (desempenho). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo `UseReadOnly`,, que viola a regra e um tipo, `UseConstant`, que satisfazem a regra.

[!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
[!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]