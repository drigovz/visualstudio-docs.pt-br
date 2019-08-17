---
title: 'CA1027: Marcar enumerações com FlagsAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92b74bcf587492155445c500252ea10773a5978b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547807"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Marcar enumerações com FlagsAttribute

|||
|-|-|
|NomeDoTipo|MarkEnumsWithFlags|
|CheckId|CA1027|
|Categoria|Microsoft.Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

Os valores de uma enumeração são potências de duas ou são combinações de outros valores que são definidos na enumeração e o <xref:System.FlagsAttribute?displayProperty=fullName> atributo não está presente. Para reduzir os falsos positivos, essa regra não relata uma violação das enumerações que têm valores contíguos.

Por padrão, essa regra só examina enumerações públicas, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Aplica <xref:System.FlagsAttribute> -se a uma enumeração quando suas constantes nomeadas podem ser combinadas de uma significativa. Por exemplo, considere uma enumeração dos dias da semana em um aplicativo que controla quais recursos do dia estão disponíveis. Se a disponibilidade de cada recurso for codificada usando a enumeração que <xref:System.FlagsAttribute> está presente, qualquer combinação de dias poderá ser representada. Sem o atributo, somente um dia da semana pode ser representado.

Para campos que armazenam enumerações combináveis, os valores de enumeração individuais são tratados como grupos de bits no campo. Portanto, esses campos são, às vezes, chamados de *campos de bits*. Para combinar valores de enumeração para armazenamento em um campo de bits, use os operadores condicionais boolianos. Para testar um campo de bits para determinar se um valor de enumeração específico está presente, use os operadores lógicos boolianos. Para um campo de bits armazenar e recuperar valores de enumeração combinados corretamente, cada valor definido na enumeração deve ser uma potência de dois. A menos que isso seja feito, os operadores lógicos boolianos não poderão extrair os valores de enumeração individuais que são armazenados no campo.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, adicione <xref:System.FlagsAttribute> à enumeração.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprimir um aviso dessa regra se você não quiser que os valores de enumeração sejam combináveis.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de analisadores do [FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

No exemplo a seguir, `DaysEnumNeedsFlags` é uma enumeração que atende aos requisitos para usar <xref:System.FlagsAttribute> , mas não tem. A `ColorEnumShouldNotHaveFlag` enumeração não tem valores que são potências de dois, mas especifica <xref:System.FlagsAttribute>incorretamente. Isso viola a regra [CA2217: Não marque enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.FlagsAttribute?displayProperty=fullName>