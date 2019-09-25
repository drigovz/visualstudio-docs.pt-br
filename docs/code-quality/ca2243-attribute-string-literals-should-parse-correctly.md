---
title: 'CA2243: Literais de cadeias de caracteres de atributo devem ser analisados corretamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2627e94dbdd0504b164fee3ecd95dc99b3094db7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237825"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Literais de cadeias de caracteres de atributo devem ser analisados corretamente

|||
|-|-|
|NomeDoTipo|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa
O parâmetro literal da cadeia de caracteres de um atributo não é analisado corretamente para uma URL, GUID ou versão.

## <a name="rule-description"></a>Descrição da regra
Como os atributos são derivados <xref:System.Attribute?displayProperty=fullName>de, e os atributos são usados no momento da compilação, somente valores constantes podem ser passados para seus construtores. Os parâmetros de atributo que devem representar URLs, GUIDs e versões não podem ser <xref:System.Uri?displayProperty=fullName>digitados como <xref:System.Version?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>e, porque esses tipos não podem ser representados como constantes. Em vez disso, eles devem ser representados por cadeias de caracteres.

Como o parâmetro é digitado como uma cadeia de caracteres, é possível que um parâmetro formatado incorretamente possa ser passado no momento da compilação.

Essa regra usa uma heurística de nomenclatura para localizar parâmetros que representam um URI (Uniform Resource Identifier), um GUID (identificador global exclusivo) ou uma versão e verifica se o valor passado está correto.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Altere a cadeia de caracteres do parâmetro para uma URL, GUID ou versão formada corretamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se o parâmetro não representar uma URL, GUID ou versão.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra o código para o AssemblyFileVersionAttribute que viola essa regra.

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

A regra é disparada pelos seguintes parâmetros:

- Parâmetros que contêm ' version ' e não podem ser analisados para System. Version.

- Parâmetros que contêm ' GUID ' e não podem ser analisados como System. GUID.

- Parâmetros que contêm ' URI ', ' urn ' ou ' URL ' e não podem ser analisados para System. Uri.

## <a name="see-also"></a>Consulte também

- [CA1054: Parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)