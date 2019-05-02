---
title: 'CA1714: Enums de sinalizadores devem ter nomes plurais | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ce28eeafd53feefcffd22b087fd21d302f544ca6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923352"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Enumerações de sinalizador devem ter nomes no plural
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Categoria|Microsoft.Naming|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Uma enumeração pública tem o <xref:System.FlagsAttribute?displayProperty=fullName> e seu nome não termina em '.

## <a name="rule-description"></a>Descrição da Regra
 Tipos que são marcados com <xref:System.FlagsAttribute> têm nomes que estão no plurais porque o atributo indica que mais de um valor pode ser especificado. Por exemplo, uma enumeração que define os dias da semana pode ser destinada para uso em um aplicativo onde você pode especificar vários dias. Esta enumeração deve ter o <xref:System.FlagsAttribute> e poderia ser chamado 'Dias'. Uma enumeração semelhante que permite que um único dia seja especificada não teria o atributo e pode ser chamado 'Day'.

 Convenções de nomenclatura de fornecem uma aparência comum para bibliotecas que direcionam o common language runtime. Isso reduz a curva de aprendizado que é necessário para novas bibliotecas de software e aumenta a confiança do cliente que a biblioteca foi desenvolvida por alguém que tenha experiência em desenvolvimento de código gerenciado.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Verifique o nome da enumeração uma palavra no plural ou remova o <xref:System.FlagsAttribute> atributo se vários valores de enumeração não devem ser especificados simultaneamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir uma violação, se o nome é uma palavra no plural, mas não termina com do '. Por exemplo, se a enumeração de vários dias que foi descrita anteriormente foram nomeada 'DaysOfTheWeek', isso violaria a lógica da regra, mas não sua intenção. Tais violações devem ser suppressd.

## <a name="related-rules"></a>Regras relacionadas
 [CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName> [Enum Design](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
