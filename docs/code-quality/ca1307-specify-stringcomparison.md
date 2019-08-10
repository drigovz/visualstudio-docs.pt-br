---
title: 'CA1307: Especificar StringComparison'
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
ms.openlocfilehash: ce2da2c1ff5b2f74d8b4d6341050c1895b68955a
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922288"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison

|||
|-|-|
|NomeDoTipo|SpecifyStringComparison|
|CheckId|CA1307|
|Categoria|Microsoft. Globalization|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método <xref:System.StringComparison> que não define um parâmetro.

## <a name="rule-description"></a>Descrição da regra
Muitas operações de cadeia de caracteres, <xref:System.String.Compare%2A> os <xref:System.String.Equals%2A> métodos e mais importantes, fornecem uma sobrecarga <xref:System.StringComparison> que aceita um valor de enumeração como um parâmetro.

Sempre que existe uma sobrecarga que usa <xref:System.StringComparison> um parâmetro, ela deve ser usada em vez de uma sobrecarga que não usa esse parâmetro. Ao definir explicitamente esse parâmetro, seu código costuma ser mais claro e mais fácil de manter.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere os métodos de comparação de cadeia de caracteres para sobrecargas que aceitam a <xref:System.StringComparison> enumeração como um parâmetro. Por exemplo: alterar `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra quando a biblioteca ou o aplicativo for destinado a um público local limitado e, portanto, não será localizado.

## <a name="see-also"></a>Consulte também

- [Avisos de globalização](../code-quality/globalization-warnings.md)
- [CA1309: Usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)