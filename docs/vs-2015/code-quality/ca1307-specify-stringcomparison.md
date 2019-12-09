---
title: 'CA1307: especifique StringComparison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 111f0b85a601d931ac17bde46f7170fa81e71815
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661406"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: especificar StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SpecifyStringComparison|
|CheckId|CA1307|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro <xref:System.StringComparison>.

## <a name="rule-description"></a>Descrição da Regra
 Muitas operações de cadeia de caracteres, mais importantes os métodos <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A>, fornecem uma sobrecarga que aceita um valor de enumeração <xref:System.StringComparison> como um parâmetro.

 Sempre que existe uma sobrecarga que usa um parâmetro <xref:System.StringComparison>, ela deve ser usada em vez de uma sobrecarga que não usa esse parâmetro. Ao definir explicitamente esse parâmetro, seu código costuma ser mais claro e mais fácil de manter.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere os métodos de comparação de cadeia de caracteres para sobrecargas que aceitem a enumeração <xref:System.StringComparison> como um parâmetro. Por exemplo: altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo for destinado a um público local limitado e, portanto, não será localizado.

## <a name="see-also"></a>Consulte também
 [Avisos de globalização](../code-quality/globalization-warnings.md) [CA1309: usar ordinal StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)
