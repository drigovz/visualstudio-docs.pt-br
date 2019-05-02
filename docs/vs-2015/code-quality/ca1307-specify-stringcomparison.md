---
title: 'CA1307: Especificar StringComparison | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 292e174feeb123c640306bc8ef3ffedd7e8847f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926338"
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: Especificar StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|SpecifyStringComparison|
|CheckId|CA1307|
|Categoria|Microsoft.Globalization|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Uma operação de comparação de cadeia de caracteres usa uma sobrecarga de método não define uma <xref:System.StringComparison> parâmetro.

## <a name="rule-description"></a>Descrição da Regra
 Muitas operações, mais importante da cadeia de caracteres a <xref:System.String.Compare%2A> e <xref:System.String.Equals%2A> métodos, fornecer uma sobrecarga que aceita um <xref:System.StringComparison> valor de enumeração como um parâmetro.

 Sempre que uma sobrecarga existe que utiliza um <xref:System.StringComparison> parâmetro, ele deve ser usado em vez de uma sobrecarga que não utilize esse parâmetro. Definindo explicitamente esse parâmetro, seu código é geralmente feita mais clara e fácil de manter.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere métodos de comparação de cadeia de caracteres para sobrecargas que aceitam o <xref:System.StringComparison> enumeração como um parâmetro. Por exemplo: altere `String.Compare(str1, str2)` para `String.Compare(str1, str2, StringComparison.Ordinal)`.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, quando a biblioteca ou o aplicativo é destinado a um público limitado de local e, portanto, não será localizado.

## <a name="see-also"></a>Consulte também
 [Avisos de globalização](../code-quality/globalization-warnings.md) [CA1309: Usar StringComparison ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)
