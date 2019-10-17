---
title: 'CA1304: especificar CultureInfo'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f4726b21b51b963074ee9ae1c161872f6a5e5a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444441"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: especificar CultureInfo

|||
|-|-|
|NomeDoTipo|SpecifyCultureInfo|
|CheckId|CA1304|
|Categoria|Microsoft. Globalization|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um método ou construtor chama um membro que tem uma sobrecarga que aceita um parâmetro <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> e o método ou construtor não chama a sobrecarga que usa o parâmetro <xref:System.Globalization.CultureInfo>. Essa regra ignora as chamadas para os seguintes métodos:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descrição da regra

Quando um objeto <xref:System.Globalization.CultureInfo> ou <xref:System.IFormatProvider?displayProperty=nameWithType> não é fornecido, o valor padrão fornecido pelo membro sobrecarregado pode não ter o efeito desejado em todas as localidades. Além disso, os membros do .NET escolhem a cultura e a formatação padrão com base nas suposições que podem não estar corretas para o seu código. Para garantir que o código funcione conforme o esperado para seus cenários, você deve fornecer informações específicas de cultura de acordo com as seguintes diretrizes:

- Se o valor for exibido para o usuário, use a cultura atual. Consulte <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Se o valor for armazenado e acessado pelo software, ou seja, persistido em um arquivo ou banco de dados, use a cultura invariável. Consulte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Se você não souber o destino do valor, faça com que o consumidor ou o provedor de dados especifique a cultura.

Mesmo que o comportamento padrão do membro sobrecarregado seja apropriado para suas necessidades, é melhor chamar explicitamente a sobrecarga específica da cultura para que seu código seja autodocumentado e mais facilmente mantido.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> é usado somente para recuperar recursos localizados usando uma instância da classe <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, use a sobrecarga que usa um argumento <xref:System.Globalization.CultureInfo>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra quando estiver certo de que a cultura padrão é a opção correta e onde a manutenção do código não é uma prioridade de desenvolvimento importante.

## <a name="example-showing-how-to-fix-violations"></a>Exemplo mostrando como corrigir violações

No exemplo a seguir, `BadMethod` causa duas violações dessa regra. `GoodMethod` corrige a primeira violação passando a cultura invariável para <xref:System.String.Compare%2A?displayProperty=nameWithType> e corrige a segunda violação passando a cultura atual para <xref:System.String.ToLower%2A?displayProperty=nameWithType>, pois `string3` é exibido para o usuário.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Exemplo mostrando saída formatada

O exemplo a seguir mostra o efeito da cultura atual no padrão <xref:System.IFormatProvider> que é selecionado pelo tipo <xref:System.DateTime>.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Este exemplo gera a seguinte saída:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Regras relacionadas

- [CA1305: especificar IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Consulte também

- [Usando a classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)
