---
title: 'CA1712: Não prefixar valores de enumeração com um nome de tipo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 323025eb03d2a949a970659aba2357c01ed8bfab
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921756"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Não prefixar valores de enumeração com um nome de tipo

|||
|-|-|
|NomeDoTipo|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Uma enumeração contém um membro cujo nome começa com o nome do tipo da enumeração.

## <a name="rule-description"></a>Descrição da regra
Os nomes dos membros de enumeração não são prefixados com o nome do tipo porque as informações de tipo devem ser fornecidas pelas ferramentas de desenvolvimento.

As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz o tempo necessário para que o aprenda uma nova biblioteca de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, remova o prefixo do nome do tipo do membro da enumeração.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma enumeração nomeada incorretamente seguida da versão corrigida.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1711: Os identificadores não devem ter um sufixo incorreto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Enum?displayProperty=fullName>