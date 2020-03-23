---
title: Como compilar um projeto que tem recursos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a76246096eec8779ce331e93f01be5ab791d1cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633948"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Como criar um projeto que tem recursos

Se você estiver compilando versões localizadas de um projeto, todos os elementos da interface do usuário devem ser separados em arquivos de recursos para os diferentes idiomas. Se o projeto usar somente cadeias de caracteres, os arquivos de recursos poderão usar arquivos de texto. Alternativamente, você pode usar arquivos *.resx* como arquivos de recursos.

## <a name="compile-resources-with-msbuild"></a>Compilar recursos com o MSBuild

A biblioteca de tarefas comuns fornecidas com `GenerateResource` o MSBuild inclui uma tarefa que você pode usar para compilar recursos em arquivos *.resx* ou texto. Esta tarefa inclui o parâmetro `Sources` para especificar quais arquivos de recurso compilar e o parâmetro `OutputResources` para especificar nomes para os arquivos de recurso de saída. Para obter mais `GenerateResource` informações sobre a tarefa, consulte [Gerar recurso .](../msbuild/generateresource-task.md)

#### <a name="to-compile-resources-with-msbuild"></a>Para compilar recursos com o MSBuild

1. Identifique os arquivos de recurso do projeto e passe-os para a tarefa `GenerateResource`, como listas de itens ou como nomes de arquivo.

2. Especifique o parâmetro `OutputResources` da tarefa `GenerateResource`, que permite que você defina os nomes para os arquivos de recurso de saída.

3. Use o elemento `Output` da tarefa para armazenar o valor do parâmetro `OutputResources` em um item.

4. Use o item criado do elemento `Output` como uma entrada em outra tarefa.

## <a name="example"></a>Exemplo

O exemplo de código a seguir mostra como o elemento `Output` especifica que o atributo `OutputResources` da tarefa `GenerateResource` conterá os arquivos de recurso compilados *alpha.resources* e *beta.resources* e que esses dois arquivos serão colocados na lista de itens `Resources`. Ao identificar esses arquivos *.resources* como uma coleção de itens de mesmo nome, você pode facilmente usá-los como entradas para outra tarefa, como a tarefa [CSC.](../msbuild/csc-task.md)

Essa tarefa é equivalente a usar o comutador **/compile** para [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example"></a>Exemplo

O exemplo de projeto a seguir contém duas tarefas: a tarefa `GenerateResource` para compilar recursos e a tarefa `Csc` para compilar os arquivos de código-fonte e os arquivos de recurso compilados. Os arquivos de recurso compilados pela tarefa `GenerateResource` são armazenados no item `Resources` e passados para a tarefa `Csc`.

```xml
<Project DefaultTargets = "Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <Target Name="Resources">
        <GenerateResource
            Sources="alpha.resx; beta.txt"
            OutputResources="alpha.resources; beta.resources">
            <Output TaskParameter="OutputResources"
                ItemName="Resources"/>
        </GenerateResource>
    </Target>

    <Target Name="Build" DependsOnTargets="Resources">
        <Csc Sources="hello.cs"
                Resources="@(Resources)"
                OutputAssembly="hello.exe"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
- [Tarefa GenerateResource](../msbuild/generateresource-task.md)
- [Tarefa csc](../msbuild/csc-task.md)
- [Resgen.exe (Gerador de Arquivo de Recurso)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
