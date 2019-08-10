---
title: 'CA1309: Usar StringComparison ordinal'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c528266c54bbb2f3f0d9420461d700a46b09bd5
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922278"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Usar StringComparison ordinal

|||
|-|-|
|NomeDoTipo|UseOrdinalStringComparison|
|CheckId|CA1309|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

Uma operação de comparação de cadeia de caracteres não lingüística não define <xref:System.StringComparison> o parâmetro como **ordinal** ou **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descrição da regra
Muitas operações de cadeia de caracteres, <xref:System.String.Compare%2A?displayProperty=fullName> mais <xref:System.String.Equals%2A?displayProperty=fullName> importante, os métodos e, agora fornecem uma <xref:System.StringComparison?displayProperty=fullName> sobrecarga que aceita um valor de enumeração como um parâmetro.

Quando você especifica **StringComparison. Ordinal** ou **StringComparison. OrdinalIgnoreCase**, a comparação de cadeia de caracteres é não lingüística. Ou seja, os recursos que são específicos para o idioma natural são ignorados quando as decisões de comparação são feitas. Ignorar recursos de linguagem natural significa que as decisões são baseadas em comparações de byte simples e não em maiúsculas ou minúsculas ou tabelas de equivalência que são parametrizadas por cultura. Como resultado, definir explicitamente o parâmetro como **StringComparison. Ordinal** ou **StringComparison. OrdinalIgnoreCase**, seu código geralmente ganha velocidade, aumenta a exatidão e se torna mais confiável.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o método de comparação de cadeia de caracteres para uma sobrecarga <xref:System.StringComparison?displayProperty=fullName> que aceite a enumeração como um parâmetro e especifique o **ordinal** ou **OrdinalIgnoreCase**. Por exemplo, altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo se destina a um público local limitado ou quando a semântica da cultura atual deve ser usada.

## <a name="see-also"></a>Consulte também

- [Avisos de globalização](../code-quality/globalization-warnings.md)
- [CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)