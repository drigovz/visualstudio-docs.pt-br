---
title: Elemento Choose (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 966e942fbd32841bbfe0a429c8623da09dcbbd0f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593363"
---
# <a name="choose-element-msbuild"></a>Elemento Choose (MSBuild)
Avalia a elementos filho para selecionar um conjunto de elementos `ItemGroup` e/ou `PropertyGroup` a ser avaliado.

 \<projeto > \<escolha > \<quando > \<escolha >... \<caso contrário > \<escolha >...

## <a name="syntax"></a>Sintaxe

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.

### <a name="attributes"></a>{1&gt;{2&gt;Atributos&lt;2}&lt;1}
 Nenhuma.

### <a name="child-elements"></a>Child elements

|Elemento|Descrição|
|-------------|-----------------|
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Elemento opcional.<br /><br /> Especifica o bloco de código `PropertyGroup` e os elementos `ItemGroup` para avaliar se as condições de todos os elementos `When` correspondem a `false`. Pode haver um zero ou um elemento `Otherwise` em um elemento `Choose`, e ele deve ser o último elemento.|
|[When](../msbuild/when-element-msbuild.md)|Elemento obrigatório.<br /><br /> Especifica um possível bloco de códigos para o elemento `Choose` selecionar. Pode haver um ou mais elementos `When` em um elemento `Choose`.|

### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |
| - | - |
| [Otherwise](../msbuild/otherwise-element-msbuild.md) | Especifica o bloco de código a ser executado se as condições de todos os elementos `When` forem avaliadas como `false`. |
| [Projeto](../msbuild/project-element-msbuild.md) | Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| [When](../msbuild/when-element-msbuild.md) | Especifica um possível bloco de códigos para o elemento `Choose` selecionar. |

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
- [Constructos condicionais](../msbuild/msbuild-conditional-constructs.md)
- [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)
