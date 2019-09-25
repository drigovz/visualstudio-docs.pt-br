---
title: 'CA1008: Enumerações devem ter valor zero'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236498"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Enumerações devem ter valor zero

|||
|-|-|
|NomeDoTipo|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Categoria|Microsoft.Design|
|Alteração significativa|Sem interrupção – quando você for solicitado a adicionar um valor **None** a uma enumeração sem sinalizador. Quebra-quando você é solicitado a renomear ou remover qualquer valor de enumeração.|

## <a name="cause"></a>Causa

Uma enumeração sem um aplicado <xref:System.FlagsAttribute?displayProperty=fullName> não define um membro que tenha um valor igual a zero. Ou, uma enumeração que tem um aplicado <xref:System.FlagsAttribute> define um membro que tem um valor igual a zero, mas seu nome não é ' nenhum '. Ou, a enumeração define vários membros com valor zero.

Por padrão, essa regra só examina enumerações visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

O valor padrão de uma enumeração não inicializada, assim como outros tipos de valor, é zero. Uma enumeração não atribuída por sinalizadores deve definir um membro que tenha o valor de zero para que o valor padrão seja um valor válido da enumeração. Se apropriado, nomeie o membro como "nenhum". Caso contrário, atribua zero ao membro usado com mais frequência. Por padrão, se o valor do primeiro membro de enumeração não estiver definido na declaração, seu valor será zero.

Se uma enumeração que tem o <xref:System.FlagsAttribute> aplicado definir um membro com valor zero, seu nome deverá ser ' none ' para indicar que nenhum valor foi definido na enumeração. O uso de um membro de valor zero para qualquer outra finalidade é diferente do uso do <xref:System.FlagsAttribute> , pois os operadores and e or não são inúteis com o membro. Isso implica que apenas um membro deve receber o valor zero. Se vários membros que têm o valor zero ocorrerem em uma enumeração atribuída por sinalizadores `Enum.ToString()` , o retorna resultados incorretos para membros que não são zero.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra para enumerações não atribuídas a sinalizadores, defina um membro que tenha o valor de zero; Essa é uma alteração sem interrupção. Para enumerações atribuídas a sinalizadores que definem um membro com valor zero, nomeie este membro como ' none ' e exclua todos os outros membros que tenham um valor de zero; Essa é uma alteração significativa.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir um aviso dessa regra, exceto para enumerações atribuídas a sinalizadores que foram enviadas anteriormente.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra duas enumerações que satisfazem a regra e uma `BadTraceOptions`enumeração,, que viola a regra.

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700: Não Nomeie os valores de enumeração como ' reservado '](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712: Não Prefixe valores de enumeração com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028: O armazenamento de enumeração deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Enum?displayProperty=fullName>