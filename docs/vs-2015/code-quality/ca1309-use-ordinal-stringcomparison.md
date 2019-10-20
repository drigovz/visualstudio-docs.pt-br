---
title: 'CA1309: usar StringComparison ordinal | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34054f6f444e503077c1e81da9f08ae2832d635a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661426"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: usar StringComparison ordinal
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseOrdinalStringComparison|
|CheckId|CA1309|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Uma operação de comparação de cadeia de caracteres não lingüística não define o parâmetro <xref:System.StringComparison> como **ordinal** ou **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descrição da Regra
 Muitas operações de cadeia de caracteres, mais importantes os métodos <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName>, agora fornecem uma sobrecarga que aceita um valor de enumeração <xref:System.StringComparison?displayProperty=fullName> como um parâmetro.

 Quando você especifica **StringComparison. Ordinal** ou **StringComparison. OrdinalIgnoreCase**, a comparação de cadeia de caracteres será não lingüística. Ou seja, os recursos que são específicos para o idioma natural são ignorados quando as decisões de comparação são feitas. Isso significa que as decisões são baseadas em comparações de byte simples e ignoram maiúsculas ou minúsculas ou tabelas de equivalência que são parametrizadas por cultura. Como resultado, definir explicitamente o parâmetro como **StringComparison. Ordinal** ou **StringComparison. OrdinalIgnoreCase**, seu código geralmente ganha velocidade, aumenta a exatidão e se torna mais confiável.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o método de comparação de cadeia de caracteres para uma sobrecarga que aceite a enumeração <xref:System.StringComparison?displayProperty=fullName> como um parâmetro e especifique o **ordinal** ou **OrdinalIgnoreCase**. Por exemplo, altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo é destinado a um público local limitado ou quando a semântica da cultura atual deve ser usada.

## <a name="see-also"></a>Consulte também
 [Avisos de globalização](../code-quality/globalization-warnings.md) [CA1307: especifique StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
