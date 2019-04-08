---
title: 'CA2226: Operadores devem ter sobrecargas simétricas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a903fbd3b01523a86302b58f8e9a74917312566c
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873224"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Operadores devem ter sobrecargas simétricas

|||
|-|-|
|NomeDoTipo|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um tipo implementa o operador de igualdade ou de desigualdade e não implementa o operador oposto.

Por padrão, essa regra olha apenas tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Não há nenhuma circunstância onde igualdade ou desigualdade é aplicável a instâncias de um tipo, e o operador oposto é indefinido. Tipos normalmente implementam o operador de desigualdade, retornando o valor negado do operador de igualdade.

O compilador C# emite um erro para as violações dessa regra.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, implementar a igualdade e os operadores de desigualdade, ou remover o que está presente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Se você fizer isso, seu tipo não funcionará de maneira consistente com o .NET.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```
dotnet_code_quality.ca2226.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (uso). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1046: Não sobrecarregar operador equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225: Sobrecargas de operador possuem alternativas nomeadas](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2224: Substituir equals ao sobrecarregar operador equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: o operador de sobrecarga é igual ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)