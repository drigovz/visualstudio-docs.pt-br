---
title: 'CA2104: Não declarar tipos de referência mutáveis somente leitura'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232961"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Não declarar tipos de referência mutáveis somente leitura

|||
|-|-|
|NomeDoTipo|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Categoria|Microsoft.Security|
|Alteração significativa|Sem interrupção|

> [!NOTE]
> A regra CA2104 é obsoleta e será removida em uma versão futura do Visual Studio. Ele não será implementado como um [analisador](roslyn-analyzers-overview.md) devido à análise complicada que é necessária para determinar a imutabilidade real de um tipo.

## <a name="cause"></a>Causa

Um tipo visível externamente contém um campo somente leitura visível externamente que é um tipo de referência mutável.

## <a name="rule-description"></a>Descrição da regra

Um tipo mutável é um tipo cujos dados da instância podem ser modificados. A <xref:System.Text.StringBuilder?displayProperty=fullName> classe é um exemplo de um tipo de referência mutável. Ele contém membros que podem alterar o valor de uma instância da classe. Um exemplo de um tipo de referência imutável é a <xref:System.String?displayProperty=fullName> classe. Depois de ter sido instanciado, seu valor nunca pode ser alterado.

O modificador somente leitura ([ReadOnly](/dotnet/csharp/language-reference/keywords/readonly) em C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) em Visual Basic e [const](/cpp/cpp/const-cpp) in C++) em um campo de tipo de referência (ou ponteiro C++em) impede que o campo seja substituído por uma instância diferente do tipo de referência. No entanto, o modificador não impede que os dados da instância do campo sejam modificados por meio do tipo de referência.

Essa regra pode mostrar inadvertidamente uma violação para um tipo que é, de fato, imutável. Nesse caso, é seguro suprimir o aviso.

Os [campos de matriz somente leitura são isentos dessa regra, mas, em vez disso, causam uma violação do CA2105: Os campos de matriz não devem ser](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regra somente leitura.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o modificador somente leitura ou, se uma alteração significativa for aceitável, substitua o campo por um tipo imutável.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra se o tipo de campo for imutável.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma declaração de campo que causa uma violação dessa regra:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]