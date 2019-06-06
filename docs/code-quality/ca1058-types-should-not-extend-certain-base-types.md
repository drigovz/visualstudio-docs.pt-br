---
title: 'CA1058: Tipos não devem estender determinados tipos base'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4157316756e4b180f6fb49082bf60927ddb43707
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714801"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Tipos não devem estender determinados tipos base

|||
|-|-|
|NomeDoTipo|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo estende um dos seguintes tipos de base:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

Por padrão, essa regra olha apenas tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

As exceções devem derivar <xref:System.Exception?displayProperty=fullName> ou uma de suas subclasses no <xref:System> namespace.

Não crie uma subclasse de <xref:System.Xml.XmlDocument> se você deseja criar uma exibição XML de uma fonte de dados ou modelo de objeto subjacente.

### <a name="non-generic-collections"></a>Coleções não genéricas

Usar e/ou estender coleções genéricas, sempre que possível. Não estenda coleções não genéricas no seu código, a menos que você o enviados anteriormente.

**Exemplos de uso incorreto**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

**Exemplos de uso correto**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, derive o tipo de um tipo base diferente ou uma coleção genérica.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir um aviso nessa regra quanto a violações sobre <xref:System.ApplicationException>. É seguro suprimir um aviso nessa regra quanto a violações sobre <xref:System.Xml.XmlDocument>. É seguro suprimir um aviso sobre uma coleção não genéricas se o código foi lançado anteriormente.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1058.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).