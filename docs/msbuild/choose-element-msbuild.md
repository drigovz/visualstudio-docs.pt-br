---
title: Elemento Choose (MSBuild) | Microsoft Docs
description: Use o elemento Choose do MSBuild para avaliar os elementos filho e selecione um conjunto de elementos rowgroup ou PropertyGroup para avaliar.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ad83bc215c70389dbb9383e1cb9562b99be7106
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796622"
---
# <a name="choose-element-msbuild"></a>Elemento Choose (MSBuild)

Avalia a elementos filho para selecionar um conjunto de elementos `ItemGroup` e/ou `PropertyGroup` a ser avaliado.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Sintaxe

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

 nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[,](../msbuild/otherwise-element-msbuild.md)|Elemento opcional.<br /><br /> Especifica o bloco de código `PropertyGroup` e os elementos `ItemGroup` para avaliar se as condições de todos os elementos `When` correspondem a `false`. Pode haver um zero ou um elemento `Otherwise` em um elemento `Choose`, e ele deve ser o último elemento.|
|[Ao](../msbuild/when-element-msbuild.md)|Elemento necessário.<br /><br /> Especifica um possível bloco de códigos para o elemento `Choose` selecionar. Pode haver um ou mais elementos `When` em um elemento `Choose`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [,](../msbuild/otherwise-element-msbuild.md) | Especifica o bloco de código a ser executado se as condições de todos os elementos `When` forem avaliadas como `false`. |
| [Projeto](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto do MSBuild. |
| [Ao](../msbuild/when-element-msbuild.md) | Especifica um possível bloco de códigos para o elemento `Choose` selecionar. |

## <a name="remarks"></a>Comentários

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

## <a name="see-also"></a>Veja também

- [Construções condicionais](../msbuild/msbuild-conditional-constructs.md)
- [Referência de esquema de arquivo de projeto](../msbuild/msbuild-project-file-schema-reference.md)
