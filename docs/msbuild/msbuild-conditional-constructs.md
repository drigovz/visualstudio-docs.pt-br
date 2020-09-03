---
title: Constructos condicionais do MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7d6693a24d208cab6bd3b58ce16dcba8a32b190
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184283"
---
# <a name="msbuild-conditional-constructs"></a>Constructos condicionais do MSBuild

O MSBuild fornece um mecanismo para processamento ou/ou com os elementos [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md)e [otherwise](../msbuild/otherwise-element-msbuild.md) .

## <a name="use-the-choose-element"></a>Usar o elemento Choose

 O elemento `Choose` contém uma série de elementos de `When` com atributos `Condition` que são testados na ordem de cima para baixo até que um seja avaliado como `true`. Se mais de um elemento `When` for avaliado como `true`, somente o primeiro será usado. Um elemento `Otherwise`, se presente, será avaliado se nenhuma condição em um elemento `When` for avaliada como `true`.

 Os elementos `Choose` podem ser usados como elementos filhos dos elementos `Project`, `When` e `Otherwise`. Os elementos `When` e `Otherwise` podem ter elementos filho `ItemGroup`, `PropertyGroup` ou `Choose`.

## <a name="example"></a>Exemplo

 O exemplo a seguir usa os elementos `Choose` e `When` para processamento de um/ou outro. As propriedades e os itens do projeto são definidos dependendo do valor da propriedade `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
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
    </Choose>
    <!-- Rest of Project -->
</Project>
```

Neste exemplo, é usada uma condição em uma constante de compilador `DEFINED_CONSTANT` . Eles são incluídos na `DefinedConstants` propriedade. A expressão regular é usada para corresponder a constante exata em uma lista separada por ponto-e-vírgula.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>Confira também

- [Escolher elemento (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)
- [Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
