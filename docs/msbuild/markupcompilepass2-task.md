---
title: Tarefa MarkupCompilePass2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633519"
---
# <a name="markupcompilepass2-task"></a>Tarefa MarkupCompilePass2

A <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tarefa executa a compilação de marcação de segundo passo em arquivos XAML que fazem referência a tipos no mesmo projeto.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | Descrição |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parâmetro **booliano** opcional.<br /><br /> Especifica se a tarefa deve ser executada em um <xref:System.AppDomain> separado. Se esse parâmetro retornar **false**, a tarefa será executada na mesma <xref:System.AppDomain> forma que o MSBuild e será executada mais rapidamente. Se o parâmetro retornar **true**, a tarefa será executada em um segundo <xref:System.AppDomain> que é isolada do MSBuild e executada mais devagar. |
| `AssembliesGeneratedDuringBuild` | Parâmetro opcional de **cadeia de caracteres []** .<br /><br /> Especifica as referências aos assemblies alterados durante o processo de build. Por exemplo, uma solução do Visual Studio pode conter um projeto que faz referência à saída compilada de outro projeto. Nesse caso, a saída compilada do segundo projeto pode ser adicionada a **AssembliesGeneratedDuringBuild**.<br /><br /> Observação: **AssembliesGeneratedDuringBuild** deve conter referências ao conjunto completo de assemblies que são gerados por uma solução de build. |
| `AssemblyName` | Parâmetro obrigatório **String**.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto. Por exemplo, se um projeto estiver gerando um executável cujo nome é *WinExeAssembly.exe*, o parâmetro **AssemblyName** terá um valor de **WinExeAssembly**. |
| `GeneratedBaml` | Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Contém a lista de arquivos gerados no formato binário XAML. |
| `KnownReferencePaths` | Parâmetro opcional de **cadeia de caracteres []** .<br /><br /> Especifica as referências aos assemblies nunca alterados durante o processo de build. Inclui assemblies que estão localizados no GAC (cache de assembly global), em um diretório de instalação do .NET e assim por diante. |
| `Language` | Parâmetro obrigatório **String**.<br /><br /> Especifica a linguagem gerenciada à qual o compilador dá suporte. As opções válidas são **C#**, **VB**, **JScript** e **C++**. |
| `LocalizationDirectivesToLocFile` | Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica como gerar informações de localização para cada arquivo XAML de origem. As opções válidas são **None**, **CommentsOnly** e **All**. |
| `OutputPath` | Parâmetro obrigatório **String**.<br /><br /> Especifica o diretório no qual os arquivos de formato binário XAML gerados são gerados. |
| `OutputType` | Parâmetro obrigatório **String**.<br /><br /> Especifica o tipo de assembly que é gerado por um projeto. As opções válidas são **winexe**, **exe**, **library** e **netmodule**. |
| `References` | Parâmetro opcional **ITaskItem []** .<br /><br /> Especifica a lista de referências de arquivos para assemblies que contêm os tipos usados nos arquivos XAML. Uma referência é ao assembly gerado pela tarefa <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, que deve ser executada antes da tarefa <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o namespace raiz para as classes que estão dentro do projeto. **RootNamespace** também é usado como o namespace padrão de um arquivo de código gerenciado gerado quando o arquivo XAML correspondente não inclui o `x:Class` atributo. |
| `XAMLDebuggingInformation` | Parâmetro **booliano** opcional.<br /><br /> Quando **true**, as informações de diagnóstico são geradas e incluídas no XAML compilado para auxiliar na depuração. |

## <a name="remarks"></a>Comentários

Antes de executar o **MarkupCompilePass2**, você deve gerar um assembly temporário que contenha os tipos que são usados pelos arquivos XAML cuja passagem de compilação de marcação foi adiada. Gere o assembly temporário executando a tarefa **GenerateTemporaryTargetAssembly**.

Uma referência ao assembly temporário gerado é fornecida quando é <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> executada, permitindo que os arquivos XAML cuja compilação foi adiada na primeira passagem de compilação de marcação agora sejam compilados para o formato binário.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar a tarefa <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> para executar uma compilação de segunda passagem.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência do MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas do WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefa do MSBuild](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Visão geral dos aplicativos de navegador XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
