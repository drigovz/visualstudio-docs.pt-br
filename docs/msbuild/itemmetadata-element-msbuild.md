---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
description: Saiba mais sobre o elemento do MSBuild ItemMetadata, que contém uma chave de metadados de item definida pelo usuário que tem o valor de metadados.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f48c57769ff6f969e68a50418b017d9928149fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913816"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)

Contém uma chave de metadados de item definida pelo usuário, que contém o valor de metadados do item. Um item pode ter qualquer número de pares de chave-valor de metadados.

 \<Project> \<ItemGroup>
 \<Item>

## <a name="syntax"></a>Sintaxe

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Condition`|Atributo opcional.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementos filho

 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Um elemento definido pelo usuário que define as entradas para o processo de build.|

## <a name="text-value"></a>Valor de texto

 Um valor de texto é opcional.

 Esse texto Especifica o valor de metadados do item, que pode ser texto ou XML.

## <a name="example"></a>Exemplo

 O exemplo de código a seguir mostra como adicionar metadados de `Culture` com o valor `fr` ao item `CSFile`.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Confira também

- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
- [Itens](../msbuild/msbuild-items.md)
