---
title: 'CA1801: Examinar parâmetros não utilizados'
ms.date: 06/24/2019
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a73ce207d8efb0c6309ba52648c7231f89bc7984
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766051"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Examinar parâmetros não utilizados

|||
|-|-|
|NomeDoTipo|ReviewUnusedParameters|
|CheckId|CA1801|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável – se o membro não estiver visível fora do assembly, independentemente da alteração feita.<br /><br /> Não separável – se você alterar o membro para usar o parâmetro dentro de seu corpo.<br /><br /> Quebrando – se você remover o parâmetro e ele estiver visível fora do assembly.|

## <a name="cause"></a>Causa

Uma assinatura de método inclui um parâmetro que não é usado no corpo do método.

Essa regra não examina os seguintes tipos de métodos:

- Métodos referenciados por um delegado.

- Métodos usados como manipuladores de eventos.

- Métodos declarados `abstract` com`MustOverride` o modificador (no Visual Basic).

- Métodos declarados `virtual` com`Overridable` o modificador (no Visual Basic).

- Métodos declarados `override` com`Overrides` o modificador (no Visual Basic).

- Métodos declarados `extern` com`Declare` o modificador (instrução no Visual Basic).

Se você estiver usando [analisadores do FxCop](install-fxcop-analyzers.md), essa regra não sinalizará parâmetros que são nomeados com o símbolo de [descarte](/dotnet/csharp/discards) , `_`por `_1`exemplo, `_2`, e. Isso reduz o ruído de aviso nos parâmetros necessários para os requisitos de assinatura, por exemplo, um método usado como um delegado, um parâmetro com atributos especiais ou um parâmetro cujo valor é acessado implicitamente em tempo de execução por uma estrutura, mas não é referenciado no auto-completar.

## <a name="rule-description"></a>Descrição da regra

Examine os parâmetros em métodos não virtuais que não são usados no corpo do método para garantir que não exista incorreta em relação a falhas para acessá-los. Os parâmetros não utilizados incorrem em custos de desempenho e manutenção.

Às vezes, uma violação dessa regra pode apontar para um bug de implementação no método. Por exemplo, o parâmetro deve ter sido usado no corpo do método. Suprimir avisos dessa regra se o parâmetro precisar existir devido à compatibilidade com versões anteriores.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o parâmetro não utilizado (uma alteração significativa) ou use o parâmetro no corpo do método (uma alteração não significativa).

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso desta regra:

- No código anteriormente enviado para o qual a correção seria uma alteração significativa.

- Para o `this` parâmetro em um método de extensão personalizado <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=nameWithType>para. As funções na <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> classe são estáticas, portanto, não é necessário acessar o `this` parâmetro no corpo do método.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra dois métodos. Um método viola a regra e o outro método satisfaz a regra.

[!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

[CA1811: Evitar código particular não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Evitar classes internas não instanciadas](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Remover locais não utilizados](../code-quality/ca1804-remove-unused-locals.md)
