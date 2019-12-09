---
title: 'CA1057: sobrecargas de URI de cadeia de caracteres chamam sobrecargas de System. URI | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba7e7de4f3ef6336ed3d82dc1e1da03ec0bf2575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603073"
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057: as sobrecargas de URI da cadeia de caracteres chamam sobrecargas System.Uri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo declara sobrecargas de método que diferem apenas pela substituição de um parâmetro de cadeia de caracteres com um parâmetro <xref:System.Uri?displayProperty=fullName>, e a sobrecarga que usa o parâmetro de cadeia de caracteres não chama a sobrecarga que usa o parâmetro <xref:System.Uri>.

## <a name="rule-description"></a>Descrição da Regra
 Como as sobrecargas diferem somente pelo parâmetro String/<xref:System.Uri>, a cadeia de caracteres é considerada para representar um URI (Uniform Resource Identifier). Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A classe <xref:System.Uri> fornece esses serviços de forma segura e segura. Para colher os benefícios da classe <xref:System.Uri>, a sobrecarga da cadeia de caracteres deve chamar a sobrecarga de <xref:System.Uri> usando o argumento de cadeia de caracteres.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Reimplemente o método que usa a representação de cadeia de caracteres do URI para que ele crie uma instância da classe <xref:System.Uri> usando o argumento string e, em seguida, passe o objeto <xref:System.Uri> para a sobrecarga que tem o parâmetro <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra se o parâmetro da cadeia de caracteres não representar um URI.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra uma sobrecarga de cadeia de caracteres implementada corretamente.

 [!code-cpp[FxCop.Design.CallUriOverload#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cpp/FxCop.Design.CallUriOverload.cpp#1)]
 [!code-csharp[FxCop.Design.CallUriOverload#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/cs/FxCop.Design.CallUriOverload.cs#1)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CallUriOverload/vb/FxCop.Design.CallUriOverload.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2234: passar objetos System.Uri em vez de cadeias de caracteres](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056: as propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: os parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: os valores de retorno de URI não devem ser cadeias de caracteres](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
