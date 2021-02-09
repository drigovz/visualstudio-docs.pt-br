---
title: Como limpar um build | Microsoft Docs
description: Saiba como usar o MSBuild para limpar uma compilação, excluir todos os arquivos intermediários e de saída e deixar apenas os arquivos de projeto e de componente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6c0beb70379d8b79a3e1826ba74f34202eea19f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914452"
---
# <a name="how-to-clean-a-build"></a>Como limpar um build

Quando você limpa um build, todos os arquivos de saída e intermediários são excluídos, deixando apenas os arquivos de projeto e componente. Nos arquivos de projeto e de componente, novas instâncias dos arquivos de saída e intermediários podem ser criadas. 

## <a name="create-a-directory-for-output-items"></a>Criar um diretório para itens de saída

 Por padrão, o arquivo *.exe* criado quando você compila um projeto é colocado no mesmo diretório dos arquivos de projeto e de origem. No entanto, normalmente, itens de saída são criados em um diretório separado.

### <a name="to-create-a-directory-for-output-items"></a>Para criar um diretório para itens de saída

1. Use o elemento `Property` para definir o local e o nome do diretório. Por exemplo, crie um diretório chamado *BuiltApp* no diretório que contém os arquivos de projeto e de origem:

     `<builtdir>BuiltApp</builtdir>`

2. Use a tarefa [MakeDir](../msbuild/makedir-task.md) para criar o diretório se o diretório não existir. Por exemplo:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Remover os itens de saída

 Antes de criar novas instâncias dos arquivos de saída e intermediários, é possível limpar todas as instâncias anteriores dos arquivos de saída e intermediários. Use a tarefa [RemoveDir](../msbuild/removedir-task.md) para excluir um diretório e todos os arquivos e diretórios que ele contém de um disco.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Para remover um diretório e todos os arquivos contidos no diretório

- Use a tarefa `RemoveDir` para remover o diretório. Por exemplo:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Exemplo

 O seguinte exemplo de projeto de código contém um novo destino, `Clean`, que usa a tarefa `RemoveDir` para excluir um diretório e todos os arquivos e diretórios que ele contém. Também no exemplo, o destino `Compile` cria um diretório separado para os itens de saída que são excluídos quando o build for removida.

 `Compile` é definido como o destino padrão e, portanto, é usado automaticamente a menos que você especifique um ou mais destinos diferentes. Use a opção de linha de comando **-target** para especificar um destino diferente. Por exemplo:

 `msbuild <file name>.proj -target:Clean`

 A opção **-target** pode ser abreviada como **-t** e pode especificar mais de um destino. Por exemplo, para usar o destino `Clean` e, em seguida, o destino `Compile`, digite:

 `msbuild <file name>.proj -t:Clean;Compile`

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <!-- Set the application name as a property -->
        <name>HelloWorldCS</name>

        <!-- Set the output folder as a property -->
        <builtdir>BuiltApp</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <!-- Specify the inputs by type and file name -->
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Check whether an output folder exists and create
        one if necessary -->
        <MakeDir Directories = "$(builtdir)"
            Condition = "!Exists('$(builtdir)')" />

        <!-- Run the Visual C# compiler -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(BuiltDir)\$(appname).exe">
            <Output TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>

        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>

    <Target Name = "Clean">
        <RemoveDir Directories="$(builtdir)" />
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefa MakeDir](../msbuild/makedir-task.md)
- [Tarefa RemoveDir](../msbuild/removedir-task.md)
- [tarefa Csc](../msbuild/csc-task.md)
- [Destinos](../msbuild/msbuild-targets.md)
