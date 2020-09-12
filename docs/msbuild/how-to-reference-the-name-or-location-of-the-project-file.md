---
title: Referenciar o nome ou o local do arquivo de projeto
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29960de09b512a419a56a61f493702485c287475
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036451"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Como referenciar o nome ou o local do arquivo de projeto

Você pode usar o nome ou local do projeto no próprio arquivo de projeto sem ter de criar sua própria propriedade. O MSBuild fornece propriedades reservadas que fazem referência ao nome do arquivo de projeto e outras propriedades relacionadas ao projeto. Para obter mais informações sobre propriedades reservadas, confira [Propriedades reservadas e conhecidas do MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Usar as propriedades do projeto

 O MSBuild fornece algumas propriedades reservadas que você pode usar em seus arquivos de projeto sem defini-las a cada vez. Por exemplo, a propriedade reservada `MSBuildProjectName` fornece uma referência ao nome do arquivo de projeto. Por exemplo, a propriedade reservada `MSBuildProjectDirectory` fornece uma referência ao nome do arquivo de projeto.

#### <a name="to-use-the-project-properties"></a>Para usar as propriedades do projeto

- Faça referência à propriedade no arquivo de projeto com a notação $(), como faria com qualquer propriedade. Por exemplo:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Uma vantagem de usar uma propriedade reservada é que qualquer alteração no nome do arquivo de projeto é incorporada automaticamente. Na próxima vez que você compilar o projeto, o arquivo de saída terá o novo nome sem necessidade de ação adicional de sua parte.

  Para obter mais informações sobre o uso de caracteres especiais em referências de arquivo ou projeto, consulte [caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> As propriedades reservadas não podem ser redefinidas no arquivo de projeto.

## <a name="example"></a>Exemplo

 O arquivo de projeto de exemplo a seguir faz referência ao nome de projeto como uma propriedade reservada para especificar o nome para a saída.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Exemplo

 O arquivo de projeto de exemplo a seguir usa a propriedade reservada `MSBuildProjectDirectory` para criar o caminho completo para um arquivo no local do arquivo de projeto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

O exemplo usa a sintaxe da [função de propriedade](property-functions.md) para chamar o método de .NET Framework estático <xref:System.IO.Path.Combine*?displayProperty=fullName> .

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
- [Propriedades reservadas e conhecidas do MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
