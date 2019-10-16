---
title: 'CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd79751c67ca5540cb22eb692b2d11c0941005a6
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349048"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri

|||
|-|-|
|NomeDoTipo|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Categoria|Microsoft. Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo declara sobrecargas de método que diferem apenas pela substituição de um parâmetro de cadeia de caracteres com um parâmetro <xref:System.Uri?displayProperty=fullName>, e a sobrecarga que usa o parâmetro de cadeia de caracteres não chama a sobrecarga que usa o parâmetro <xref:System.Uri>.

## <a name="rule-description"></a>Descrição da regra
Como as sobrecargas diferem somente pelo parâmetro String ou <xref:System.Uri>, a cadeia de caracteres é considerada para representar um URI (Uniform Resource Identifier). Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A classe <xref:System.Uri> fornece esses serviços de forma segura e segura. Para colher os benefícios da classe <xref:System.Uri>, a sobrecarga da cadeia de caracteres deve chamar a sobrecarga de <xref:System.Uri> usando o argumento de cadeia de caracteres.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Reimplemente o método que usa a representação de cadeia de caracteres do URI para que ele crie uma instância da classe <xref:System.Uri> usando o argumento string e, em seguida, passe o objeto <xref:System.Uri> para a sobrecarga que tem o parâmetro <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se o parâmetro da cadeia de caracteres não representar um URI.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma sobrecarga de cadeia de caracteres implementada corretamente.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA2234: passar objetos System.Uri em vez de cadeias de caracteres](../code-quality/ca2234.md)

[CA1056: as propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: os parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: os valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)