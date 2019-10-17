---
title: 'CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86e9fe7b06f16474376d3cc672607bb2ef54746a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72438969"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: os nomes de parâmetro não devem corresponder aos nomes de membro

|||
|-|-|
|NomeDoTipo|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Categoria|Microsoft. Naming|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
O nome de um membro visível externamente corresponde a, em uma comparação que não diferencia maiúsculas de minúsculas, o nome de um de seus parâmetros.

## <a name="rule-description"></a>Descrição da regra
Um nome de parâmetro deve informar o significado de um parâmetro e um nome de membro deve informar o significado de um membro. Seria um design raro se eles fossem iguais. A nomenclatura de um parâmetro com o mesmo nome do membro não é intuitiva e dificulta o uso da biblioteca.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Selecione um nome de parâmetro que não corresponda ao nome do membro.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Para o novo desenvolvimento, nenhum cenário conhecido ocorre onde você deve suprimir um aviso dessa regra. Para as bibliotecas de envio, talvez seja necessário suprimir um aviso dessa regra.

## <a name="related-rules"></a>Regras relacionadas
[CA1709: os identificadores devem ter maiúsculas e minúsculas corretas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708: os identificadores devem ser diferentes além de maiúsculas de minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
