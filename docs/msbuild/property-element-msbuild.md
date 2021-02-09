---
title: Elemento Property (MSBuild) | Microsoft Docs
description: Saiba mais sobre o elemento de Propriedade do MSBuild, que contém um nome de propriedade definido pelo usuário e um valor que deve ser especificado como um filho de um elemento PropertyGroup.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 617a6d3712b137d76334d4063f36a1b8dde1d101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918854"
---
# <a name="property-element-msbuild"></a>Elemento Property (MSBuild)

Contém um nome e valor de propriedade definidos pelo usuário. Cada propriedade usada em um projeto do MSBuild deve ser especificada como um filho de um `PropertyGroup` elemento.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Sintaxe

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento de agrupamento para propriedades.|

## <a name="text-value"></a>Valor de texto

 Um valor de texto é opcional.

 Esse texto especifica o valor da propriedade e pode conter XML.

## <a name="remarks"></a>Comentários

 Nomes de propriedade estão limitados a apenas a caracteres ASCII. Valores de propriedades são referenciados no projeto, colocando o nome da propriedade entre "`$(`" e "`)`". Por exemplo, `$(builddir)\classes` resolveria para *build\classes*, se a propriedade `builddir` tivesse o valor `build`. Para saber mais sobre as propriedades, confira [Propriedades do MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Exemplo

 O código a seguir define a propriedade `Optimization` para `false` e a propriedade `DefaultVersion` para `1.0` se a propriedade `Version` estiver vazia.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Confira também

- [propriedades MSBuild](../msbuild/msbuild-properties.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
