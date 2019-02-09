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
ms.openlocfilehash: b00accdbdb08e4267bbca2b7e5fab8002f539f1d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922507"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309: Usar StringComparison ordinal

|||
|-|-|
|NomeDoTipo|UseOrdinalStringComparison|
|CheckId|CA1309|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Uma operação de comparação de cadeia de caracteres linguística não define o <xref:System.StringComparison> parâmetro a **Ordinal** ou **OrdinalIgnoreCase**.

## <a name="rule-description"></a>Descrição da regra
 Muitos de cadeia de caracteres operações, mais importante é que o <xref:System.String.Compare%2A?displayProperty=fullName> e <xref:System.String.Equals%2A?displayProperty=fullName> métodos, agora fornecem uma sobrecarga que aceita um <xref:System.StringComparison?displayProperty=fullName> valor de enumeração como um parâmetro.

 Quando você especificar **StringComparison. ordinal** ou **StringComparison. OrdinalIgnoreCase**, a comparação de cadeia de caracteres é não linguística. Ou seja, os recursos que são específicos para o idioma natural são ignorados quando a comparação decisões são tomadas. Ignorar os recursos de linguagem natural significa que as decisões com base em comparações de byte simples e não em maiusculas e minúsculas ou tabelas de equivalência que são parametrizadas pela cultura. Como resultado, definindo explicitamente o parâmetro como o **StringComparison. ordinal** ou **StringComparison. OrdinalIgnoreCase**, seu código normalmente ganha velocidade, aumenta a exatidão e torna-se mais confiável.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, altere o método de comparação de cadeia de caracteres para uma sobrecarga que aceita o <xref:System.StringComparison?displayProperty=fullName> enumeração como um parâmetro e especifique **Ordinal** ou **OrdinalIgnoreCase**. Por exemplo, altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 É seguro suprimir um aviso nessa regra, quando o aplicativo ou biblioteca destina-se para um público limitado de local, ou quando a semântica da cultura atual deve ser usada.

## <a name="see-also"></a>Consulte também

- [Avisos de globalização](../code-quality/globalization-warnings.md)
- [CA1307: Especificar StringComparison](../code-quality/ca1307-specify-stringcomparison.md)