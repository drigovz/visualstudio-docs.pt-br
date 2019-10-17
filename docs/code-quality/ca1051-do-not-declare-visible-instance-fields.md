---
title: 'CA1051: não declarar campos de instância visíveis'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69fb85c396da1acde40cd9bc46150ca5f1386c17
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449131"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: não declarar campos de instância visíveis

|||
|-|-|
|NomeDoTipo|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Categoria|Microsoft. Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo tem um campo de instância não privada.

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

O principal uso de um campo deve ser um como um detalhe da implementação. Os campos devem ser `private` ou `internal` e devem ser expostos usando as propriedades. É tão fácil acessar uma propriedade quanto é acessar um campo, e o código nos acessadores de uma propriedade pode ser alterado à medida que os recursos do tipo se expandem sem introduzir alterações significativas.

As propriedades que retornam apenas o valor de um campo privado ou interno são otimizadas para serem executadas em par com o acesso a um campo; o lucro de desempenho do uso de campos visíveis externamente em vez de propriedades é mínimo. *Externamente visível* refere-se aos níveis de acessibilidade `public`, `protected` e `protected internal` (`Public`, `Protected` e `Protected Friend` em Visual Basic).

Além disso, os campos públicos não podem ser protegidos por [demandas de link](/dotnet/framework/misc/link-demands). Para obter mais informações, consulte [CA2112: tipos protegidos não devem expor campos](../code-quality/ca2112.md). (As demandas de link não são aplicáveis a aplicativos .NET Core.)

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, torne o campo `private` ou `internal` e expor-o usando uma propriedade visível externamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Apenas suprimir este aviso se você tiver certeza de que os consumidores precisam de acesso direto ao campo. Para a maioria dos aplicativos, os campos expostos não fornecem benefícios de desempenho ou de manutenção em relação às propriedades.

Os consumidores podem precisar de acesso ao campo nas seguintes situações:

- em ASP.NET Web Forms controles de conteúdo
- Quando a plataforma de destino usa `ref` para modificar campos, como estruturas MVVM (Model-View-ViewModel) para WPF e UWP

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo (`BadPublicInstanceFields`) que viola essa regra. `GoodPublicInstanceFields` mostra o código corrigido.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112.md)

## <a name="see-also"></a>Consulte também

- [Demandas de link](/dotnet/framework/misc/link-demands)
