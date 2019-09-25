---
title: 'CA1700: Não nomear valores &#39;de enumeração reservados&#39;'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5171123827481c99bbc35c10b04aaf942a15fabb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234385"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: Não nomear valores &#39;de enumeração reservados&#39;

|||
|-|-|
|NomeDoTipo|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Categoria|Microsoft.Naming|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

O nome de um membro de enumeração contém a palavra "reservado".

## <a name="rule-description"></a>Descrição da regra

Esta regra pressupõe que um membro da enumeração que tenha um nome que contém "reserved" não é usado atualmente, mas é um espaço reservado a ser renomeado ou removido em uma versão futura. Renomear ou remover um membro é uma alteração drástica. Você não deve esperar que os usuários ignorem um membro apenas porque seu nome contém "reservado", nem você pode contar com os usuários para ler ou obedecer à documentação. Além disso, como os membros reservados aparecem em navegadores de objetos e em ambientes de desenvolvimento integrados inteligentes, eles podem causar confusão sobre quais membros estão realmente sendo usados.

Em vez de usar um membro reservado, adicione um novo membro à enumeração na versão futura. Na maioria dos casos, a adição do novo membro não é uma alteração significativa, contanto que a adição não cause a alteração dos valores dos membros originais.

Em um número limitado de casos, a adição de um membro é uma alteração significativa, mesmo quando os membros originais retêm seus valores originais. Principalmente, o novo membro não pode ser retornado de caminhos de código existentes sem quebrar chamadores que `switch` usam`Select` uma [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]instrução (in) no valor de retorno que abrange toda a lista de membros e que gera uma exceção no caso padrão. Uma preocupação secundária é que o código do cliente pode não lidar com a alteração no comportamento dos métodos <xref:System.Enum.IsDefined%2A?displayProperty=fullName>de reflexão, como. Da mesma forma, se o novo membro tiver de ser retornado de métodos existentes ou se uma incompatibilidade de aplicativo conhecida ocorrer devido ao mau uso da reflexão, a única solução não-separável será:

1. Adicione uma nova enumeração que contém os membros originais e novos.

2. Marque a enumeração original com o <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo.

   Siga o mesmo procedimento para qualquer tipo visível externamente ou membros que exponham a enumeração original.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova ou renomeie o membro.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra para um membro que está sendo usado no momento ou para bibliotecas que foram enviadas anteriormente.

## <a name="related-rules"></a>Regras relacionadas

[CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712: Não Prefixe valores de enumeração com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: O armazenamento de enumeração deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008: Enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)