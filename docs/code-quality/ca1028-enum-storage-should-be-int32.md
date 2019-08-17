---
title: 'CA1028: O armazenamento de enumerações deve ser Int32'
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
ms.openlocfilehash: c91de575abe8b19a5d8f6fca864e2bc452da7cb2
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547652"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: O armazenamento de enumerações deve ser Int32

|||
|-|-|
|NomeDoTipo|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

O tipo subjacente de uma enumeração não <xref:System.Int32?displayProperty=fullName>é.

Por padrão, essa regra só examina enumerações públicas, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Por padrão, o <xref:System.Int32?displayProperty=fullName> tipo de dados é usado para armazenar o valor constante. Embora você possa alterar esse tipo subjacente, ele não é necessário ou recomendado para a maioria dos cenários. Nenhum benefício de desempenho significativo é obtido com o uso de um tipo de dados <xref:System.Int32>menor que. Se você não puder usar o tipo de dados padrão, deverá usar um dos tipos integrais compatíveis com o sistema de linguagem comum ( <xref:System.Byte>CLS <xref:System.Int16>) <xref:System.Int32>,, <xref:System.Int64> , ou para garantir que todos os valores da enumeração possam ser representados em Linguagens de programação em conformidade com CLS.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, a menos que existam problemas de tamanho ou <xref:System.Int32>compatibilidade, use. Para situações em <xref:System.Int32> que não é grande o suficiente para manter os valores <xref:System.Int64>, use. Se a compatibilidade com versões anteriores exigir um tipo de <xref:System.Byte> dados <xref:System.Int16>menor, use ou.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprimir um aviso desta regra somente se os problemas de compatibilidade com versões anteriores exigirem. Em aplicativos, a falha em obedecer a essa regra geralmente não causa problemas. Em bibliotecas, em que a interoperabilidade de linguagem é necessária, a falha na conformidade com essa regra pode afetar negativamente os usuários.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de analisadores do [FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1028.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Exemplo de uma violação

O exemplo a seguir mostra duas enumerações que não usam o tipo de dados subjacente recomendado.

[!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
[!code-csharp[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]

## <a name="example-of-how-to-fix"></a>Exemplo de como corrigir

O exemplo a seguir corrige a violação anterior alterando o tipo de dados <xref:System.Int32>subjacente para.

[!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
[!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1008: Enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)
- [CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Não Nomeie os valores de enumeração como ' reservado '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Não Prefixe valores de enumeração com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Byte?displayProperty=fullName>
- <xref:System.Int16?displayProperty=fullName>
- <xref:System.Int32?displayProperty=fullName>
- <xref:System.Int64?displayProperty=fullName>