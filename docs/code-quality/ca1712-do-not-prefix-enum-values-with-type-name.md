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
ms.openlocfilehash: dd15e582f7654f82e343a0175ccf9ed18254d904
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545864"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Não prefixar valores de enumeração com um nome de tipo

|||
|-|-|
|NomeDoTipo|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma enumeração contém um membro cujo nome começa com o nome do tipo de enumeração.

## <a name="rule-description"></a>Descrição da regra
 Nomes dos membros de enumeração não são prefixados com o nome do tipo porque as informações de tipo deve ser fornecido pelas ferramentas de desenvolvimento.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz o tempo que é necessário para aprender uma nova biblioteca de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, remova o prefixo de nome de tipo do membro de enumeração.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma enumeração nomeada incorretamente seguida a versão corrigida.

 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1711: Identificadores não devem ter sufixo incorreto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Enum?displayProperty=fullName>