---
title: Como selecionar os arquivos para compilar | Microsoft Docs
description: Saiba como selecionar os arquivos a serem compilados no arquivo de projeto do MSBuild, listando cada arquivo separadamente ou usando curingas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, wildcards
- MSBuild, including files
- Include attribute [MSBuild]
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4593fff50feb0176ea81f70dc297bc39d8dd1936
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436198"
---
# <a name="how-to-select-the-files-to-build"></a>Como selecionar os arquivos a serem compilados

Quando você compila um projeto que contém vários arquivos, é possível listar cada arquivo separadamente no arquivo de projeto ou usar caracteres curinga para incluir todos os arquivos em um diretório ou um conjunto aninhado de diretórios.

## <a name="specify-inputs"></a>Especificar entradas

Os itens representam as entradas para um build. Para obter mais informações sobre os itens, consulte [Itens](../msbuild/msbuild-items.md).

Para incluir arquivos para uma compilação, eles devem ser incluídos em uma lista de itens no arquivo de projeto do MSBuild. Vários arquivos podem ser adicionados a listas de itens incluindo os arquivos individualmente ou usando caracteres curinga para incluir vários arquivos ao mesmo tempo.

#### <a name="to-declare-items-individually"></a>Para declarar itens individualmente

- Use os atributos `Include` semelhantes ao seguinte:

    `<CSFile Include="form1.cs"/>`

    ou

    `<VBFile Include="form1.vb"/>`

    > [!NOTE]
    > Se os itens em uma coleção de itens não estiverem no mesmo diretório que o arquivo de projeto, será necessário especificar o caminho completo ou relativo para o item. Por exemplo: `Include="..\..\form2.cs"`.

#### <a name="to-declare-multiple-items"></a>Para declarar vários itens

- Use os atributos `Include` semelhantes ao seguinte:

    `<CSFile Include="form1.cs;form2.cs"/>`

    ou

    `<VBFile Include="form1.vb;form2.vb"/>`

## <a name="specify-inputs-with-wildcards"></a>Especificar entradas com curingas

Você também pode usar caracteres curinga para incluir recursivamente todos os arquivos ou apenas arquivos específicos de subdiretórios como entradas para um build. Para obter mais informações sobre caracteres curinga, consulte [Itens](../msbuild/msbuild-items.md)

Os seguintes exemplos baseiam-se em um projeto que contém arquivos de elementos gráficos nos seguintes diretórios e subdiretórios, com o arquivo de projeto localizado no diretório *Project*:

*Project\Images\BestJpgs*

*Project\Images\ImgJpgs*

*Project\Images\ImgJpgs\Img1*

#### <a name="to-include-all-jpg-files-in-the-images-directory-and-subdirectories"></a>Para incluir todos os arquivos *.jpg* no diretório *Images* e nos subdiretórios

- Use o seguinte atributo `Include`:

    `Include="Images\**\*.jpg"`

#### <a name="to-include-all-jpg-files-starting-with-img"></a>Para incluir todos os arquivos *.jpg* que começam com *img*

- Use o seguinte atributo `Include`:

    `Include="Images\**\img*.jpg"`

#### <a name="to-include-all-files-in-directories-with-names-ending-in-jpgs"></a>Para incluir todos os arquivos em diretórios com nomes que terminam com *jpgs*

- Use um dos seguintes atributos `Include`:

    `Include="Images\**\*jpgs\*.*"`

    ou

    `Include="Images\**\*jpgs\*"`

## <a name="pass-items-to-a-task"></a>Passar itens para uma tarefa

Em um arquivo de projeto, você pode usar a notação @() em tarefas para especificar uma lista completa de itens como a entrada para um build. Você pode usar essa notação se listar todos os arquivos separadamente ou usar caracteres curinga.

#### <a name="to-use-all-visual-c-or-visual-basic-files-as-inputs"></a>Para usar todos os arquivos do Visual c# ou Visual Basic como entradas

- Use os atributos `Include` semelhantes ao seguinte:

    `<CSC Sources="@(CSFile)">...</CSC>`

    ou

    `<VBC Sources="@(VBFile)">...</VBC>`

> [!NOTE]
> Você deve usar caracteres curinga com itens para especificar as entradas para uma compilação; Você não pode especificar as entradas usando o `Sources` atributo em tarefas do MSBuild, como [CSC](../msbuild/csc-task.md) ou [Vbc](../msbuild/vbc-task.md). O exemplo a seguir não é válido em um arquivo de projeto:
>
> `<CSC Sources="*.cs">...</CSC>`

## <a name="example-1"></a>Exemplo 1

O exemplo de código a seguir mostra um projeto que inclui todos os arquivos de entrada separadamente.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Builtdir>built</Builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="Form1.cs"/>
        <CSFile Include="AssemblyInfo.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="example-2"></a>Exemplo 2

O exemplo de código a seguir usa um curinga para incluir todos os arquivos *.cs*.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <builtdir>built</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs"/>

        <Reference Include="System.dll"/>
        <Reference Include="System.Data.dll"/>
        <Reference Include="System.Drawing.dll"/>
        <Reference Include="System.Windows.Forms.dll"/>
        <Reference Include="System.XML.dll"/>
    </ItemGroup>

    <Target Name="PreBuild">
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>
    </Target>

    <Target Name="Compile" DependsOnTargets="PreBuild">
        <Csc Sources="@(CSFile)"
            References="@(Reference)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"
            TargetType="exe" />
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Como excluir arquivos da compilação](../msbuild/how-to-exclude-files-from-the-build.md)
- [Itens](../msbuild/msbuild-items.md)
