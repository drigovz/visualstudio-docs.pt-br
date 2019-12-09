---
title: 'CA1717: somente enumerações FlagsAttribute devem ter nomes no plural | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0c378d419be0d964c27cfcbe523fbe3a33da97b8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669092"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: apenas enums FlagsAttribute devem ter nomes plurais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Categoria|Microsoft. Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O nome de uma enumeração visível externamente termina em uma palavra plural e a enumeração não é marcada com o atributo <xref:System.FlagsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 As convenções de nomenclatura ditam que um nome no plural para uma enumeração indica que mais de um valor da enumeração pode ser especificado simultaneamente. O <xref:System.FlagsAttribute> informa aos compiladores que a enumeração deve ser tratada como um campo de bits que permite operações bit a bit na enumeração.

 Se apenas um valor de uma enumeração puder ser especificado por vez, o nome da enumeração deverá ser uma palavra singular. Por exemplo, uma enumeração que define os dias da semana pode ser destinada a uso em um aplicativo em que você pode especificar vários dias. Essa enumeração deve ter o <xref:System.FlagsAttribute> e pode ser chamada de ' Days '. Uma enumeração semelhante que permite que apenas um único dia seja especificado não teria o atributo e poderia ser chamada ' Day '.

 As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz o tempo necessário para aprender uma nova biblioteca de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Torne o nome da enumeração uma palavra singular ou adicione o <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso da regra se o nome terminar em uma palavra singular.

## <a name="related-rules"></a>Regras relacionadas
 [CA1714: enums de sinalizadores devem ter nomes plurais](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName> [design de enumeração](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
