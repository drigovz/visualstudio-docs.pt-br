---
title: 'CA1026: Parâmetros padrão não devem ser usados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 888e1b5d551e357eb732dfe3f7661d51cbdf089d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923137"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Parâmetros padrão não devem ser usados

|||
|-|-|
|NomeDoTipo|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo visível externamente contém um método visível externamente que usa um parâmetro padrão.

## <a name="rule-description"></a>Descrição da regra
Os métodos que usam parâmetros padrão são permitidos no Common Language Specification (CLS); no entanto, o CLS permite que os compiladores ignorem os valores atribuídos a esses parâmetros. O código que é escrito para compiladores que ignoram valores de parâmetro padrão deve fornecer explicitamente argumentos para cada parâmetro padrão. Para manter o comportamento que você deseja em linguagens de programação, os métodos que usam parâmetros padrão devem ser substituídos por sobrecargas de método que fornecem os parâmetros padrão.

O compilador ignora os valores dos parâmetros padrão para a extensão gerenciada C++ para quando ele acessa o código gerenciado. O compilador Visual Basic dá suporte a métodos que têm parâmetros padrão que usam a palavra-chave [opcional](/dotnet/visual-basic/language-reference/modifiers/optional) .

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, substitua o método que usa parâmetros padrão com sobrecargas de método que fornecem os parâmetros padrão.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um método que usa parâmetros padrão e os métodos sobrecarregados que fornecem uma funcionalidade equivalente.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1025: Substituir argumentos repetitivos por matriz params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Consulte também
[Componentes de independência de linguagem e componentes independentes da linguagem](/dotnet/standard/language-independence-and-language-independent-components)