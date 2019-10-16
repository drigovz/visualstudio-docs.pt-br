---
title: 'CA1712: não use valores enum como prefixo com o nome do tipo'
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
ms.openlocfilehash: f151296fce00ca92209c588c4be0361f9adfc7fd
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72348932"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: não use valores enum como prefixo com o nome do tipo

|||
|-|-|
|NomeDoTipo|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Categoria|Microsoft. Naming|
|Alteração significativa|Quebra|

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
[CA1711: os identificadores não devem ter sufixo incorreto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Enum?displayProperty=fullName>