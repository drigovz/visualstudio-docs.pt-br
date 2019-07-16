---
title: 'CA1054: Parâmetros de URI não devem ser cadeias de caracteres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f7af579cf92a785f9850805ae06743a15364eade
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200531"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054: Parâmetros de URI não devem ser cadeias de caracteres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo declara um método com um parâmetro de cadeia de caracteres cujo nome contém "uri", "Uri", "urn", "Urn", "url" ou "Url" e o tipo não declarar uma sobrecarga correspondente que utiliza um <xref:System.Uri?displayProperty=fullName> parâmetro.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra é o nome do parâmetro é dividida em tokens com base na convenção camel case e verifica se cada token é igual a "uri", "Uri", "urn", "Urn", "url" ou "Url". Se houver uma correspondência, a regra pressupõe que o parâmetro representa um uniform resource identifier (URI). Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. Se um método usa uma representação de cadeia de caracteres de um URI, uma sobrecarga correspondente deve ser fornecida utilizando uma instância da <xref:System.Uri> classe, que fornece esses serviços de maneira segura e protegida.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o parâmetro para um <xref:System.Uri> digite; essa é uma alteração significativa. Como alternativa, fornecer uma sobrecarga do método que usa um <xref:System.Uri> parâmetro; essa é uma alteração incondicional.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso nessa regra, se o parâmetro não representar um URI.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo `ErrorProne`, que viola essa regra e um tipo, `SaferWay`, que satisfaz a regra.

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1056: Propriedades URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055: Valores não devem ser cadeias de caracteres de retorno de URI](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234: Passar objetos System. URI em vez de cadeias de caracteres](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057: Cadeia de caracteres chamam sobrecargas System. URI](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
