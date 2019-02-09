---
title: 'CA2226: Operadores devem ter sobrecargas simétricas'
ms.date: 11/04/2016
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
ms.openlocfilehash: 6264b440df01e02019938eb0f742cb9789fd4f5d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931098"
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

## <a name="rule-description"></a>Descrição da regra
 Não há nenhuma circunstância onde igualdade ou desigualdade é aplicável a instâncias de um tipo, e o operador oposto é indefinido. Tipos normalmente implementam o operador de desigualdade, retornando o valor negado do operador de igualdade.

 O compilador c# emite um erro para as violações dessa regra.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, implementar a igualdade e os operadores de desigualdade, ou remover o que está presente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra. O tipo não funcionará de maneira consistente com o .NET Framework.

## <a name="related-rules"></a>Regras relacionadas
 [CA1046: Não sobrecarregar operador equals em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Sobrecargas de operador possuem alternativas nomeadas](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Substituir equals ao sobrecarregar operador equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: o operador de sobrecarga é igual ao substituir ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)