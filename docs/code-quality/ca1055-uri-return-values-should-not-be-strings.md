---
title: 'CA1055: Valores de retorno de URI não devem ser cadeias de caracteres'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6c0a03f68ed15e790ea8a43a9ae2b476dd2f6f5d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235544"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055: Valores de retorno de URI não devem ser cadeias de caracteres

|||
|-|-|
|NomeDoTipo|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

O nome de um método contém "URI", "URI", "urn", "urn", "URL" ou "URL", e o método retorna uma cadeia de caracteres.

Por padrão, essa regra só examina os métodos públicos, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Essa regra divide o nome do método em tokens com base na Convenção de maiúsculas e minúsculas do Pascal e verifica se cada token é igual a "URI", "URI", "urn", "urn", "URL" ou "URL". Se houver uma correspondência, a regra assumirá que o método retorna um URI (Uniform Resource Identifier). Uma representação de cadeia de caracteres de um URI está propensa a erros de análise e de codificação, e pode resultar em vulnerabilidades de segurança. A <xref:System.Uri?displayProperty=fullName> classe fornece esses serviços de maneira segura e segura.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere o tipo de retorno para um <xref:System.Uri>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra se o valor retornado não representar um URI.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo `ErrorProne`,, que viola essa regra e um tipo, `SaferWay`, que satisfaz a regra.

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1056: As propriedades de URI não devem ser cadeias de caracteres](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054: Parâmetros de URI não devem ser cadeias de caracteres](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234: Passar objetos System. Uri em vez de cadeias de caracteres](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057: Sobrecargas de URI de cadeia de caracteres chamam sobrecargas de System. URI](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)