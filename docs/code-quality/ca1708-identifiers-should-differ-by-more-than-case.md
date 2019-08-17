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
ms.openlocfilehash: 5098e2feadc6d67c466e31ab19d059ac70c7d833
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547406"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identificadores devem ser diferentes em algo além das maiúsculas e minúsculas

|||
|-|-|
|NomeDoTipo|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Os nomes de dois tipos, membros, parâmetros ou namespaces totalmente qualificados são idênticos quando são convertidos em minúsculas.

Por padrão, essa regra só examina os tipos, membros e namespaces visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Os identificadores de namespaces, tipos, membros e parâmetros não podem se diferenciar apenas por maiúsculas porque linguagens com o Common Language Runtime como destino não precisam diferenciar maiúsculas e minúsculas. Por exemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] é uma linguagem que não diferencia maiúsculas de minúsculas.

Esta regra é acionada somente em Membros publicamente visíveis.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Selecione um nome que seja exclusivo quando comparado a outros identificadores de uma maneira que não diferencia maiúsculas de minúsculas.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. A biblioteca pode não ser utilizável em todos os idiomas disponíveis no .NET.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de analisadores do [FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1708.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (nomenclatura). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemplo de uma violação

O exemplo a seguir demonstra uma violação dessa regra.

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1709: Os identificadores devem estar em maiúsculas e minúsculas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)