---
title: Funções de itens | Microsoft Docs
description: Saiba como o código do MSBuild em tarefas e destinos pode chamar funções de item para obter informações sobre os itens no projeto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94b94ef7b17633ab78f7eb91f61dd67ea2c8021d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904635"
---
# <a name="item-functions"></a>funções de item

O código em tarefas e destinos pode chamar funções de item para obter informações sobre os itens no projeto (no MSBuild 4,0 e posterior). Essas funções simplificam a obtenção de itens distintos e são mais rápidas do que o loop pelos itens.

## <a name="string-item-functions"></a>Funções de item de cadeia de caracteres

É possível usar métodos e propriedades de cadeia de caracteres no .NET Framework para operar em qualquer valor de item. Para métodos <xref:System.String>, especifique o nome do método. Para propriedades <xref:System.String>, especifique o nome da propriedade após "get_".

Para itens que têm várias cadeias de caracteres, o método ou propriedade da cadeia de caracteres será executado em cada cadeia de caracteres.

O exemplo a seguir mostra como usar essas funções de item de cadeia de caracteres.

```xml
<ItemGroup>
    <theItem Include="andromeda;tadpole;cartwheel" />
</ItemGroup>

<Target Name = "go">
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />
    <Message Text="Length   @(theItem->get_Length())" />
    <Message Text="Chars    @(theItem->get_Chars(2))" />
</Target>

  <!--
  Output:
    IndexOf  3;-1;2
    Replace  andromeda;pinwheel;cartwheel
    Length   9;7;9
    Chars    d;d;r
  -->
```

## <a name="intrinsic-item-functions"></a>Funções de item intrínsecas

A tabela a seguir lista as funções intrínsecas disponíveis para itens.

|Função|Exemplo|Descrição|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|Retorna a contagem dos itens.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|Retorna o equivalente de `Path.DirectoryName` para cada item.|
|`Distinct`|`@(MyItem->Distinct())`|Retorna itens com valores `Include` distintos. Os metadados são ignorados. A comparação não diferencia maiúsculas de minúsculas.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Retorna itens com valores `itemspec` distintos. Os metadados são ignorados. A comparação diferencia maiúsculas de minúsculas.|
|`Reverse`|`@(MyItem->Reverse())`|Retorna os itens em ordem inversa.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Retorna um `boolean` para indicar se qualquer item tem o valor e o nome de metadados especificado. A comparação não diferencia maiúsculas de minúsculas.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Retorna os itens com seus metadados desmarcados. Somente o `itemspec` é mantido.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Retorna os itens que têm o nome de metadados especificado. A comparação não diferencia maiúsculas de minúsculas.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Retorna os valores dos metadados que têm o nome de metadados.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Retorna os itens que têm o nome e o valor de metadados especificado. A comparação não diferencia maiúsculas de minúsculas.|

O exemplo a seguir mostra como usar funções intrínsecas de item.

```xml
<ItemGroup>
    <TheItem Include="first">
        <Plant>geranium</Plant>
    </TheItem>
    <TheItem Include="second">
        <Plant>algae</Plant>
    </TheItem>
    <TheItem Include="third">
        <Plant>geranium</Plant>
    </TheItem>
</ItemGroup>

<Target Name="go">
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />
    <Message Text=" " />
    <Message Text="Count:   @(theItem->Count())" />
    <Message Text="Reverse: @(theItem->Reverse())" />
</Target>

  <!--
  Output:
    MetaData:    geranium;algae;geranium
    HasMetadata: first;second;third
    WithMetadataValue: first;third

    Count:   3
    Reverse: third;second;first
  -->
```

## <a name="msbuild-condition-functions"></a>Funções de condição do MSBuild

As funções `Exists` e `HasTrailingSlash` não são funções de item. Eles estão disponíveis para uso com o `Condition` atributo. Consulte [condições do MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Veja também

- [Itens](../msbuild/msbuild-items.md)
