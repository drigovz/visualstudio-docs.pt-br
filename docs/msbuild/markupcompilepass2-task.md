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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633519"
---
# <a name="markupcompilepass2-task"></a>Tarefa MarkupCompilePass2

A <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> tarefa executa a compilação de marcação de segunda passagem em arquivos XAML que fazem referência a tipos no mesmo projeto.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | Descrição |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parâmetro **booleano** opcional.<br /><br /> Especifica se a tarefa deve ser executada em um <xref:System.AppDomain> separado. Se esse parâmetro retornar **falso,** a <xref:System.AppDomain> tarefa será executada no mesmo que o MSBuild e será executada mais rápido. Se o parâmetro retornar **verdadeiro,** a <xref:System.AppDomain> tarefa será executada em um segundo que é isolada do MSBuild e é executada mais lentamente. |
| `AssembliesGeneratedDuringBuild` | Parâmetro opcional **string[].**<br /><br /> Especifica as referências aos assemblies alterados durante o processo de build. Por exemplo, uma solução do Visual Studio pode conter um projeto que faz referência à saída compilada de outro projeto. Nesse caso, a saída compilada do segundo projeto pode ser adicionada a **AssembliesGeneratedDuringBuild**.<br /><br /> Observação: **AssembliesGeneratedDuringBuild** deve conter referências ao conjunto completo de assemblies que são gerados por uma solução de build. |
| `AssemblyName` | Parâmetro obrigatório **String**.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto. Por exemplo, se um projeto estiver gerando um executável cujo nome é *WinExeAssembly.exe,* o parâmetro **AssemblyName** tem um valor de **WinExeAssembly**. |
| `GeneratedBaml` | Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Contém a lista de arquivos gerados no formato binário XAML. |
| `KnownReferencePaths` | Parâmetro opcional **string[].**<br /><br /> Especifica as referências aos assemblies nunca alterados durante o processo de build. Inclui montagens localizadas no cache de montagem global (GAC), em um diretório de instalação .NET, e assim por diante. |
| `Language` | Parâmetro obrigatório **String**.<br /><br /> Especifica a linguagem gerenciada à qual o compilador dá suporte. As opções válidas são **C#**, **VB**, **JScript** e **C++**. |
| `LocalizationDirectivesToLocFile` | Parâmetro opcional **string.**<br /><br /> Especifica como gerar informações de localização para cada arquivo XAML de origem. As opções válidas são **None**, **CommentsOnly** e **All**. |
| `OutputPath` | Parâmetro obrigatório **String**.<br /><br /> Especifica o diretório no qual os arquivos de formato binário XAML gerados são gerados. |
| `OutputType` | Parâmetro obrigatório **String**.<br /><br /> Especifica o tipo de assembly que é gerado por um projeto. As opções válidas são **winexe**, **exe**, **library** e **netmodule**. |
| `References` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica a lista de referências de arquivos para conjuntos que contêm os tipos que são usados nos arquivos XAML. Uma referência é ao assembly gerado pela tarefa <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, que deve ser executada antes da tarefa <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Parâmetro opcional **string.**<br /><br /> Especifica o namespace raiz para as classes que estão dentro do projeto. **RootNamespace** também é usado como o namespace padrão de um arquivo de código `x:Class` gerenciado gerado quando o arquivo XAML correspondente não inclui o atributo. |
| `XAMLDebuggingInformation` | Parâmetro **booleano** opcional.<br /><br /> Quando **verdadeira,** as informações de diagnóstico são geradas e incluídas no XAML compilado para auxiliar na depuração. |

## <a name="remarks"></a>Comentários

Antes de executar **markupCompilePass2,** você deve gerar um conjunto temporário que contenha os tipos que são usados pelos arquivos XAML cujo passe de compilação de marcação foi adiado. Gere o assembly temporário executando a tarefa **GenerateTemporaryTargetAssembly**.

Uma referência à montagem temporária gerada <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> é fornecida para quando for executada, permitindo que os arquivos XAML cuja compilação foi adiada no primeiro passe de compilação de marcação sejam agora compilados para o formato binário.

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

- [Referência WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Referência de tarefas do WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de tarefa do MSBuild](../msbuild/msbuild-task-reference.md)
- [Compilar um aplicativo WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Visão geral dos aplicativos do navegador WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
