---
title: 'CA1307: especificar StringComparison'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3b3d979910883f6be9f542ec581ecbda0f91deb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444377"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: especificar StringComparison

|||
|-|-|
|NomeDoTipo|SpecifyStringComparison|
|CheckId|CA1307|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método que não define um parâmetro <xref:System.StringComparison>.

## <a name="rule-description"></a>Descrição da regra
Muitas operações de cadeia de caracteres, mais importantes os métodos <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A>, fornecem uma sobrecarga que aceita um valor de enumeração <xref:System.StringComparison> como um parâmetro.

Sempre que existe uma sobrecarga que usa um parâmetro <xref:System.StringComparison>, ela deve ser usada em vez de uma sobrecarga que não usa esse parâmetro. Ao definir explicitamente esse parâmetro, seu código costuma ser mais claro e mais fácil de manter.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere os métodos de comparação de cadeia de caracteres para sobrecargas que aceitem a enumeração <xref:System.StringComparison> como um parâmetro. Por exemplo: altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo for destinado a um público local limitado e, portanto, não será localizado.

## <a name="see-also"></a>Consulte também

- [Avisos de globalização](../code-quality/globalization-warnings.md)
- [CA1309: usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
