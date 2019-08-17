---
title: 'CA1051: Não declarar campos de instância visíveis'
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
ms.openlocfilehash: c5dd8a4b2d0b32a8c52f75dee6fd765a7ea6ec9a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547561"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Não declarar campos de instância visíveis

|||
|-|-|
|NomeDoTipo|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo tem um campo de instância não privada.

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

O principal uso de um campo deve ser um como um detalhe da implementação. Os campos devem `private` ser `internal` ou devem ser expostos usando propriedades. É tão fácil acessar uma propriedade quanto é acessar um campo, e o código nos acessadores de uma propriedade pode ser alterado à medida que os recursos do tipo se expandem sem introduzir alterações significativas. As propriedades que retornam apenas o valor de um campo privado ou interno são otimizadas para serem executadas em par com o acesso a um campo; um pequeno lucro de desempenho está associado ao uso de campos externos visíveis em Propriedades.

Externamente visível refere- `public`se aos níveis `protected internal` de`Public`acessibilidade `Protected`, `protected`, `Protected Friend` e (, e em Visual Basic).

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, torne o campo `private` ou `internal` Expor-o usando uma propriedade externamente visível.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Os campos visíveis externamente não fornecem nenhum benefício que não esteja disponível para propriedades. Além disso, os campos públicos não podem ser protegidos por demandas de [link](/dotnet/framework/misc/link-demands). Consulte [CA2112: Os tipos protegidos não devem expor](../code-quality/ca2112-secured-types-should-not-expose-fields.md)campos.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de analisadores do [FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo`BadPublicInstanceFields`() que viola essa regra. `GoodPublicInstanceFields`mostra o código corrigido.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA2112: Tipos protegidos não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Consulte também

- [Demandas de link](/dotnet/framework/misc/link-demands)