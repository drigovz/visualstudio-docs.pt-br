---
title: Tarefa GenerateTemporaryTargetAssembly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69333b87720513244e90c131f052d11099b62e35
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634039"
---
# <a name="generatetemporarytargetassembly-task"></a>Tarefa GenerateTemporaryTargetAssembly

A tarefa <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> gera um assembly se pelo menos uma página XAML em um projeto referencia um tipo declarado localmente nesse projeto. O assembly gerado será removido após concluir o processo de build ou se o processo de build falhar.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | DESCRIÇÃO |
|--------------------------| - |
| `AssemblyName` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto e também é o nome do assembly de destino que é gerado temporariamente. Por exemplo, se um projeto gera um executável do Windows cujo nome é *WinExeAssembly. exe*, o parâmetro **AssemblyName** tem um valor de **WinExeAssembly**. |
| `CompileTargetName` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o nome do destino do MSBuild que é usado para gerar assemblies de arquivos de código-fonte. O valor típico para **CompileTargetName** é **CoreCompile**. |
| `CompileTypeName` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o tipo de compilação é executada pelo destino que é especificado pelo parâmetro **CompileTargetName**. Para o destino **CoreCompile**, esse valor é **Compile**. |
| `CurrentProject` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o caminho completo do arquivo de projeto do MSBuild para o projeto que requer um assembly de destino temporário. |
| `GeneratedCodeFiles` | Parâmetro opcional **ITaskItem[]** .<br /><br /> Especifica a lista de arquivos de código gerenciado específicos a um idioma que foram gerados pela tarefa [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md). |
| `IntermediateOutputPath` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o diretório em que o assembly de destino temporário é gerado. |
| `MSBuildBinPath` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o local do *MSBuild.exe*, que é necessário para compilar o assembly de destino temporário. |
| `ReferencePath` | Parâmetro opcional **ITaskItem[]** .<br /><br /> Especifica uma lista de assemblies, pelo caminho e nome de arquivo, que são referenciados pelos tipos que são compilados no assembly de destino temporário. |
| `ReferencePathTypeName` | Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Especifica o parâmetro usado pelo parâmetro do destino de compilação (**CompileTargetName**) que especifica a lista de referências de assembly (**ReferencePath**). O valor apropriado é **ReferencePath**. |

## <a name="remarks"></a>Comentários

A primeira passagem de compilação de marcação, que é executada pelo [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compila arquivos XAML em formato binário. Consequentemente, o compilador precisa de uma lista dos assemblies referenciados que contêm os tipos usados pelos arquivos XAML. No entanto, se um arquivo XAML usar um tipo definido no mesmo projeto, um assembly correspondente para esse projeto não será criado até que o projeto seja compilado. Portanto, uma referência de assembly não pode ser fornecida durante a primeira passagem de compilação de marcação.

Em vez disso, **MarkupCompilePass1** adia a conversão de arquivos XAML que contêm referências a tipos no mesmo projeto para uma segunda passagem de compilação de marcação, que é executada pelo [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Antes de **MarkupCompilePass2** ser executada, um assembly temporário é gerado. Esse assembly contém os tipos que são usados pelos arquivos XAML cuja passagem de compilação de marcação foi adiada. Uma referência ao assembly gerado é fornecida ao **MarkupCompilePass2** quando ele é executado para permitir que os arquivos XAML de compilação adiada sejam convertidos em formato binário.

## <a name="example"></a>Exemplo

O exemplo a seguir gera um assembly temporário porque *Page1.xaml* contém uma referência a um tipo que está no mesmo projeto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Visão geral dos aplicativos de navegador XAML do WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
