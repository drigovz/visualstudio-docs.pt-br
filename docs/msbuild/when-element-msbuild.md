---
title: Elemento When (MSBuild) | Microsoft Docs
description: Saiba mais sobre o elemento MSBuild When, que especifica um possível bloco de código para o elemento Choose a ser selecionado.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 36d96eacc0fbc88a3fcf082493e064a77c5c403a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933811"
---
# <a name="when-element-msbuild"></a>Elemento When (MSBuild)

Especifica um possível bloco de códigos para o elemento `Choose` selecionar.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Sintaxe

```xml
<When Condition="'StringA'=='StringB'">
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</When>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|Condição|Atributo obrigatório.<br /><br /> Condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Escolha](../msbuild/choose-element-msbuild.md)|Elemento opcional.<br /><br /> Avalia elementos filhos para selecionar uma seção do código para executar. Pode ser que não haja nenhum ou mais de um elemento `Choose` em um elemento `When`.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contém um conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos pelo usuário. Pode ser que não haja nenhum ou mais de um elemento `ItemGroup` em um elemento `When`.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contém um conjunto de definidos elementos [Property](../msbuild/property-element-msbuild.md) definidos pelo usuário. Pode ser que não haja nenhum ou mais de um elemento `PropertyGroup` em um elemento `When`.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Escolher elemento (MSBuild)](../msbuild/choose-element-msbuild.md)|Avalia elementos filhos para selecionar uma seção do código para executar.|

## <a name="remarks"></a>Comentários

 Se o atributo `Condition` for avaliado como verdadeiro, os elementos `ItemGroup` filho e `PropertyGroup` do elemento `When` serão executados e todos os elementos `When` subsequentes serão ignorados.

 Os elementos `Choose`, `When` e `Otherwise` são usados juntos para fornecer uma maneira de selecionar uma seção de código para executar entre diversas possíveis alternativas. Para obter mais informações, confira [Constructos condicionais](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Exemplo

 O seguinte projeto usa o `Choose` elemento para selecionar o conjunto de valores de propriedades no elemento `When` a ser definido. Se os `Condition` atributos de ambos `When` elementos são avaliadas como `false`, os valores de propriedades no elemento `Otherwise` são definidos.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
    </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Confira também

- [Construções condicionais](../msbuild/msbuild-conditional-constructs.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
