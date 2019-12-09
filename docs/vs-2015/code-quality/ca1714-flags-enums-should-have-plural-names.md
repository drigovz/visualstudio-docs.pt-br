---
title: 'CA1714: sinalizadores Enums devem ter nomes no plural | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca3709411f50d0b65f33bb8eed6457cfd1325ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669133"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: os enums de sinalizadores devem ter nomes plurais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Categoria|Microsoft. Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma enumeração pública tem o <xref:System.FlagsAttribute?displayProperty=fullName> e seu nome não termina em ' s'.

## <a name="rule-description"></a>Descrição da Regra
 Os tipos que são marcados com <xref:System.FlagsAttribute> têm nomes que são plural porque o atributo indica que mais de um valor pode ser especificado. Por exemplo, uma enumeração que define os dias da semana pode ser destinada a uso em um aplicativo em que você pode especificar vários dias. Essa enumeração deve ter o <xref:System.FlagsAttribute> e pode ser chamada de ' Days '. Uma enumeração semelhante que permite que apenas um único dia seja especificado não teria o atributo e poderia ser chamada ' Day '.

 As convenções de nomenclatura fornecem uma aparência comum para as bibliotecas direcionadas ao Common Language Runtime. Isso reduz a curva de aprendizado necessária para novas bibliotecas de software e aumenta a confiança do cliente de que a biblioteca foi desenvolvida por alguém que tenha experiência no desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Torne o nome da enumeração uma palavra plural ou remova o atributo <xref:System.FlagsAttribute> se vários valores de enumeração não devem ser especificados simultaneamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma violação se o nome for uma palavra plural, mas não terminar em ' s'. Por exemplo, se a enumeração de vários dias que foi descrita anteriormente era denominada ' DaysOfTheWeek ', isso violaria a lógica da regra, mas não sua intenção. Essas violações devem ser suprimidas.

## <a name="related-rules"></a>Regras relacionadas
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName> [design de enumeração](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
