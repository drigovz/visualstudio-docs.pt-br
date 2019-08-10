---
title: 'CA1057: Sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri'
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
ms.openlocfilehash: 41d3db6e4807c77236868e3ab5746da971ddce6c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922487"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: Sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri

|||
|-|-|
|NomeDoTipo|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Categoria|Microsoft.Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo declara sobrecargas de método que diferem apenas pela substituição de um parâmetro de cadeia <xref:System.Uri?displayProperty=fullName> de caracteres por um parâmetro, e a sobrecarga que usa o parâmetro de cadeia de caracteres não <xref:System.Uri> chama a sobrecarga que usa o parâmetro.

## <a name="rule-description"></a>Descrição da regra
Como as sobrecargas diferem apenas pela cadeia <xref:System.Uri> de caracteres ou pelo parâmetro, a cadeia de caracteres é considerada para representar um URI (Uniform Resource Identifier). Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A <xref:System.Uri> classe fornece esses serviços de maneira segura e segura. Para colher os benefícios da <xref:System.Uri> classe, a sobrecarga da cadeia de caracteres deve chamar a <xref:System.Uri> sobrecarga usando o argumento string.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Reimplemente o método que usa a representação de cadeia de caracteres do URI para que ele crie uma <xref:System.Uri> instância da classe usando o argumento string e, em <xref:System.Uri> seguida, passe o objeto para a <xref:System.Uri> sobrecarga que tem o parâmetro.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se o parâmetro da cadeia de caracteres não representar um URI.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma sobrecarga de cadeia de caracteres implementada corretamente.

[!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
[!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
[!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA2234: Passar objetos System. Uri em vez de cadeias de caracteres](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1056: As propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1054: Parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

[CA1055: Os valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)