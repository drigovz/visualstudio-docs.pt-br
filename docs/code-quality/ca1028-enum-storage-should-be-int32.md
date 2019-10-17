---
title: 'CA1028: o armazenamento de enum deve ser Int32'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ece210d20a675cf2f55b5b619a1c1b526638582
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449229"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: o armazenamento de enum deve ser Int32

|||
|-|-|
|NomeDoTipo|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Categoria|Microsoft. Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

O tipo subjacente de uma enumeração não é <xref:System.Int32?displayProperty=fullName>.

Por padrão, essa regra só examina enumerações públicas, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Por padrão, o tipo de dados <xref:System.Int32?displayProperty=fullName> é usado para armazenar o valor constante. Embora você possa alterar esse tipo subjacente, ele não é necessário ou recomendado para a maioria dos cenários. Nenhum benefício de desempenho significativo é obtido com o uso de um tipo de dados menor que <xref:System.Int32>. Se você não puder usar o tipo de dados padrão, deverá usar um dos tipos integrais compatíveis com o sistema de linguagem comum (CLS), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> ou <xref:System.Int64> para garantir que todos os valores da enumeração possam ser representados na programação em conformidade com CLS Idiomas.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, a menos que existam problemas de tamanho ou compatibilidade, use <xref:System.Int32>. Para situações em que <xref:System.Int32> não é grande o suficiente para manter os valores, use <xref:System.Int64>. Se a compatibilidade com versões anteriores exigir um tipo de dados menor, use <xref:System.Byte> ou <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprimir um aviso desta regra somente se os problemas de compatibilidade com versões anteriores exigirem. Em aplicativos, a falha em obedecer a essa regra geralmente não causa problemas. Em bibliotecas, em que a interoperabilidade de linguagem é necessária, a falha na conformidade com essa regra pode afetar negativamente os usuários.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemplo de uma violação

O exemplo a seguir mostra duas enumerações que não usam o tipo de dados subjacente recomendado.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemplo de como corrigir

O exemplo a seguir corrige a violação anterior alterando o tipo de dados subjacente para <xref:System.Int32>.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1008: as enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217.md)
- [CA1700: não nomear valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: não usar valores de enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>
