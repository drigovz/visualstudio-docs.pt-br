---
title: 'CA1056: Propriedades URI não devem ser cadeias de caracteres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2515c88204369a96a48496e0692190e264e0eadd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924983"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056: Propriedades de URI não devem ser cadeias de caracteres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo declara uma propriedade de cadeia de caracteres cujo nome contém "uri", "Uri", "urn", "Urn", "url" ou "Url".

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é o nome da propriedade é dividida em tokens com base na convenção de maiusculas e minúsculas de Pascal e verifica se cada token é igual a "uri", "Uri", "urn", "Urn", "url" ou "Url". Se houver uma correspondência, a regra pressupõe que a propriedade representa um uniform resource identifier (URI). Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. O <xref:System.Uri?displayProperty=fullName> classe fornece esses serviços de maneira segura e protegida.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere a propriedade para um <xref:System.Uri> tipo.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se a propriedade não representa um URI.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `ErrorProne`, que viola essa regra e um tipo, `SaferWay`, que satisfaz a regra.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1054: Parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: Valores não devem ser cadeias de caracteres de retorno de URI](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Passar objetos System. URI em vez de cadeias de caracteres](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Cadeia de caracteres chamam sobrecargas System. URI](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
