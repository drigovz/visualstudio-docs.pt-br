---
title: 'CA1708: Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 059770b28b9e885608769f3844f91097a16d66cf
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714249"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas

|||
|-|-|
|NomeDoTipo|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Os nomes dos dois tipos, membros, parâmetros ou espaços para nomes totalmente qualificados são idênticos quando forem convertidos em minúsculas.

Por padrão, essa regra olha apenas para namespaces, membros e tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. Por exemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] é uma linguagem diferencia maiusculas de minúsculas amplamente utilizada.

Essa regra é acionada em apenas a membros publicamente visível.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Selecione um nome exclusivo quando comparado a outros identificadores no diferenciando maiusculas de minúsculas.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. A biblioteca não pode ser utilizada em todos os idiomas disponíveis no .NET.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1708.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (nomenclatura). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemplo de uma violação

O exemplo a seguir demonstra uma violação dessa regra.

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1709: Identificadores devem ter maiusculas e minúsculas corretamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)