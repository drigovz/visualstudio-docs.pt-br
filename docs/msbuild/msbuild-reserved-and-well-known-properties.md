---
title: Propriedades reservadas e conhecidas do MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633246"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propriedades reservadas e conhecidas do MSBuild

O MSBuild fornece um conjunto de propriedades predefinidas que armazenam informações sobre o arquivo de projeto e os binários do MSBuild. Essas propriedades são avaliadas da mesma maneira que outras propriedades do MSBuild. Por exemplo, para usar a propriedade `MSBuildProjectFile`, digite `$(MSBuildProjectFile)`.

 O MSBuild usa os valores na tabela a seguir para predefinir propriedades conhecidas e reservadas. As propriedades reservadas não podem ser substituídas, mas as propriedades conhecidas podem ser substituídas usando propriedades de ambiente com o mesmo nome, propriedades globais ou propriedades que são declaradas no arquivo de projeto.

## <a name="reserved-and-well-known-properties"></a>Propriedades reservadas e conhecidas

 A tabela a seguir descreve as propriedades predefinidas do MSBuild.

| Propriedade | Reservadas ou conhecidas | DESCRIÇÃO |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Reservado | O caminho absoluto da pasta em que os binários do MSBuild que estão sendo usados no momento estão localizados (por exemplo, *C:\Windows\Microsoft.Net\Framework\\\<versionNumber >* ). Essa propriedade será útil se você precisar se referir a arquivos no diretório do MSBuild.<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildExtensionsPath` | Conhecidas | Apresentado no .NET Framework 4: não há diferença entre os valores padrão de `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`. Você pode definir a variável de ambiente `MSBUILDLEGACYEXTENSIONSPATH` como um valor não nulo para habilitar o comportamento do valor padrão de `MSBuildExtensionsPath` em versões anteriores.<br /><br /> No .NET Framework 3.5 e anterior, o valor padrão de `MSBuildExtensionsPath` aponta para o caminho da subpasta MSBuild na pasta *\Program Files\\* ou *\Program Files (x86)* , dependendo do número de bit do processo atual. Por exemplo, para um processo de 32 bits em um computador de 64 bits, essa propriedade aponta para a pasta *\Program Files (x86)* . Para um processo de 64 bits em um computador de 64 bits, essa propriedade aponta para a pasta *\Program Files*.<br /><br /> Não inclua a barra invertida final nessa propriedade.<br /><br /> Esse local é um local útil para colocar os arquivos de destino personalizados. Por exemplo, os arquivos de destino podem ser instalados em *\Program Files\MSBuild\MyFiles\Northwind.targets* e, em seguida, importados em arquivos de projeto usando este código XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Conhecidas | O caminho da subpasta MSBuild na pasta *\Program Files* ou *\Program Files (x86)* . O caminho sempre aponta para a pasta *\Arquivos de Programas (x86)* de 32 bits em um computador de 32 bits e para *\Arquivos de Programas* em um computador de 64 bits. Consulte também `MSBuildExtensionsPath` e `MSBuildExtensionsPath64`.<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildExtensionsPath64` | Conhecidas | O caminho da subpasta MSBuild na pasta *\Program Files* . Para um computador de 64 bits, esse caminho sempre aponta para a pasta *\Program Files*. Para uma máquina de 32 bits, esse caminho fica em branco. Consulte também `MSBuildExtensionsPath` e `MSBuildExtensionsPath32`.<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildInteractive` | Reservado | `true` se o MSBuild estiver em execução interativamente, permitindo a entrada do usuário. Essa configuração é controlada pela opção de linha de comando `-interactive`. |
| `MSBuildLastTaskResult` | Reservado | `true` se a tarefa anterior foi concluída sem erros (mesmo se houver avisos) ou `false` se a tarefa anterior tiver erros. Normalmente, quando ocorre um erro em uma tarefa, o erro é a última coisa que ocorre nesse projeto. Portanto, o valor dessa propriedade nunca é `false`, exceto nestes cenários:<br /><br /> - Quando o atributo `ContinueOnError` do [elemento Task (MSBuild)](../msbuild/task-element-msbuild.md) é definido como `WarnAndContinue` (ou `true`) ou `ErrorAndContinue`.<br /><br /> - Quando o `Target` tem um [elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) como um elemento filho. |
| `MSBuildNodeCount` | Reservado | O número máximo de processos simultâneos que são usados durante a compilação. Esse é o valor especificado para **-maxcpucount** na linha de comando. Se você especificou **-maxcpucount** sem especificar um valor, então `MSBuildNodeCount` especificará o número de processadores no computador. Para saber mais, confira [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md) e [Compilar vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Reservado | O local da pasta do programa de 32 bits; por exemplo, *C:\Program Files (x86)* .<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildProjectDefaultTargets` | Reservado | A lista completa de destinos que estão especificados no atributo `DefaultTargets` do elemento `Project`. Por exemplo, o seguinte elemento `Project` teria um valor da propriedade `MSBuildDefaultTargets` de `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Reservado | O caminho absoluto do diretório em que o arquivo de projeto está localizado, por exemplo *C:\MyCompany\MyProduct*.<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildProjectDirectoryNoRoot` | Reservado | O valor da propriedade `MSBuildProjectDirectory`, excluindo a unidade raiz.<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildProjectExtension` | Reservado | A extensão de nome de arquivo do arquivo de projeto, incluindo o ponto; por exemplo, *.proj*. |
| `MSBuildProjectFile` | Reservado | O nome de arquivo completo do arquivo de projeto, incluindo a extensão de nome de arquivo; por exemplo, *MyApp.proj*. |
| `MSBuildProjectFullPath` | Reservado | O caminho absoluto e o nome de arquivo completo do arquivo de projeto, incluindo a extensão de nome de arquivo; por exemplo, *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Reservado | O nome do arquivo de projeto sem a extensão de nome de arquivo; por exemplo, *MyApp*. |
| `MSBuildRuntimeType` | Reservado | O tipo de runtime que está sendo executado. Introduzido no MSBuild 15. O valor pode ser indefinido (antes do MSBuild 15), `Full` indicando que o MSBuild está em execução no .NET Framework da área de trabalho, `Core` indicando que o MSBuild está em execução no .NET Core (por exemplo, no `dotnet build`) ou `Mono` indicando que o MSBuild está em execução no mono. |
| `MSBuildStartupDirectory` | Reservado | O caminho absoluto da pasta em que o MSBuild é chamado. Usando essa propriedade, você pode criar tudo abaixo de um ponto específico em uma árvore de projeto sem criar arquivos *\<dirs>.proj* em cada diretório. Em vez disso, você tem apenas um projeto – por exemplo, *c:\traversal.proj*, conforme mostrado aqui:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Para compilar em qualquer ponto da árvore, digite:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Não inclua a barra invertida final nessa propriedade. |
| `MSBuildThisFile` | Reservado | O nome do arquivo e a parte da extensão do arquivo de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Reservado | A parte do diretório de `MSBuildThisFileFullPath`.<br /><br /> Inclua a barra invertida final no caminho. |
| `MSBuildThisFileDirectoryNoRoot` | Reservado | A parte do diretório de `MSBuildThisFileFullPath`, excluindo a unidade raiz.<br /><br /> Inclua a barra invertida final no caminho. |
| `MSBuildThisFileExtension` | Reservado | A parte da extensão do nome de arquivo de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Reservado | O caminho absoluto do projeto ou do arquivo de destinos que contém o destino que está sendo executado.<br /><br /> Dica: você pode especificar um caminho relativo em um arquivo de destino que é relativo ao arquivo de destino e não relativo ao arquivo de projeto original. |
| `MSBuildThisFileName` | Reservado | A parte do nome de arquivo de `MSBuildThisFileFullPath`, sem a extensão de nome de arquivo. |
| `MSBuildToolsPath` | Reservado | O caminho de instalação da versão do MSBuild associada ao valor de `MSBuildToolsVersion`.<br /><br /> Não inclua a barra invertida final no caminho.<br /><br /> Essa propriedade não pode ser substituída. |
| `MSBuildToolsVersion` | Reservado | A versão do conjunto de ferramentas do MSBuild que é usada para compilar o projeto.<br /><br /> Observação: um conjunto de ferramentas do MSBuild consiste em tarefas, destinos e ferramentas que são usadas para criar um aplicativo. As ferramentas incluem compiladores, como *csc.exe* e *vbc.exe*. Para saber mais, confira [Conjunto de ferramentas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) e [Configurações padrão e personalizadas do conjunto de ferramentas](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Reservado | A versão do MSBuild usada para compilar o projeto. <br /><br/> Essa propriedade não pode ser substituída, caso contrário, a mensagem de erro `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` é retornada. |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nomes em conflito com elementos do MSBuild

Além do citado acima, os nomes que correspondem a elementos da linguagem do MSBuild não podem ser usados para propriedades, itens ou metadados de item definidos pelo usuário:

* VisualStudioProject
* Destino
* PropertyGroup
* Saída
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* Quando
* Otherwise

## <a name="see-also"></a>Confira também

- [Referência do MSBuild](../msbuild/msbuild-reference.md)

- [Propriedades do MSBuild](../msbuild/msbuild-properties.md)
