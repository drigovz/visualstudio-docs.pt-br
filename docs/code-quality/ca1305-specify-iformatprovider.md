---
title: 'CA1305: Especificar IFormatProvider'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a9f6c8fd44749de43d86bf8037df0130ad682321
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235041"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Especificar IFormatProvider

|||
|-|-|
|NomeDoTipo|SpecifyIFormatProvider|
|CheckId|CA1305|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método ou construtor chama um ou mais membros que têm sobrecargas que aceitam <xref:System.IFormatProvider?displayProperty=fullName> um parâmetro e o método ou construtor não chama a sobrecarga que usa o <xref:System.IFormatProvider> parâmetro.

Essa regra ignora as chamadas para métodos .net documentados como ignorando o <xref:System.IFormatProvider> parâmetro. A regra também ignora os seguintes métodos:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descrição da regra

Quando um <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objeto <xref:System.IFormatProvider> ou não é fornecido, o valor padrão fornecido pelo membro sobrecarregado pode não ter o efeito desejado em todas as localidades. Além disso, os membros do .NET escolhem a cultura e a formatação padrão com base nas suposições que podem não estar corretas para o seu código. Para garantir que o código funcione conforme o esperado para seus cenários, você deve fornecer informações específicas de cultura de acordo com as seguintes diretrizes:

- Se o valor for exibido para o usuário, use a cultura atual. Consulte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Se o valor for armazenado e acessado pelo software (persistido em um arquivo ou banco de dados), use a cultura invariável. Consulte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Se você não souber o destino do valor, faça com que o consumidor ou o provedor de dados especifique a cultura.

Mesmo que o comportamento padrão do membro sobrecarregado seja apropriado para suas necessidades, é melhor chamar explicitamente a sobrecarga específica da cultura para que seu código seja autodocumentado e mais facilmente mantido.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, use a sobrecarga que usa um <xref:System.IFormatProvider> argumento. Ou use uma [ C# cadeia de caracteres interpolada](/dotnet/csharp/tutorials/string-interpolation) e passe-a <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> para o método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra quando tiver certeza de que o formato padrão é a opção correta e onde a manutenção do código não é uma prioridade de desenvolvimento importante.

## <a name="example"></a>Exemplo

No código a seguir, a `example1` cadeia de caracteres viola a regra CA1305. A `example2` cadeia de caracteres satisfaz a regra CA1305 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>passando, que <xref:System.IFormatProvider>implementa, <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>para. A `example3` cadeia de caracteres satisfaz a regra CA1305 ao passar uma cadeia de <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>caracteres interpolada para.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Regras relacionadas

- [CA1304: Especificar CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Consulte também

- [Usando a classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)