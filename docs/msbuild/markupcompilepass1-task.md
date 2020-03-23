---
title: Tarefa MarkupCompilePass1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a847f096edf5e42623cb2cb32cf4fd871a89aad7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633506"
---
# <a name="markupcompilepass1-task"></a>Tarefa MarkupCompilePass1

A <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tarefa converte arquivos de projeto XAML não localizados em formato binário compilado.

## <a name="task-parameters"></a>Parâmetros de tarefa

| Parâmetro | Descrição |
| - | - |
| `AllGeneratedFiles` | Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Contém uma lista completa dos arquivos que são gerados pela tarefa <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Parâmetro **booleano** opcional.<br /><br /> Especifica se a tarefa deve ser executada em um <xref:System.AppDomain> separado. Se esse parâmetro retornar **falso,** a <xref:System.AppDomain> tarefa será executada no mesmo que o MSBuild e será executada mais rápido. Se o parâmetro retornar **verdadeiro,** a <xref:System.AppDomain> tarefa será executada em um segundo que é isolada do MSBuild e é executada mais lentamente. |
| `ApplicationMarkup` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica o nome do arquivo XAML de definição de aplicativo. |
| `AssembliesGeneratedDuringBuild` | Parâmetro opcional **string[].**<br /><br /> Especifica as referências aos assemblies alterados durante o processo de build. Por exemplo, uma solução do Visual Studio pode conter um projeto que faz referência à saída compilada de outro projeto. Nesse caso, a saída compilada do segundo projeto pode ser adicionada ao parâmetro **AssembliesGeneratedDuringBuild**.<br /><br /> Observação: o parâmetro **AssembliesGeneratedDuringBuild** deve conter referências ao conjunto completo de assemblies que são gerados por uma solução de build. |
| `AssemblyName` | Parâmetro de **corda** necessário.<br /><br /> Especifica o nome curto do assembly que é gerado para um projeto. Por exemplo, se um projeto estiver gerando um executável do Windows cujo nome é *WinExeAssembly.exe,* o parâmetro **AssemblyName** tem um valor de **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Parâmetro opcional **string.**<br /><br /> Especifica o token da chave pública para o assembly. |
| `AssemblyVersion` | Parâmetro opcional **string.**<br /><br /> Especifica o número de versão do assembly. |
| `ContentFiles` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica a lista de arquivos de conteúdo flexível. |
| `DefineConstants` | Parâmetro opcional **string.**<br /><br /> Especifica que o valor atual de **DefineConstants** é mantido. que afeta a geração de montagem alvo; se esse parâmetro for alterado, a API pública no conjunto de destino pode ser alterada e a compilação de arquivos XAML que fazem referência aos tipos locais pode ser afetada. |
| `ExtraBuildControlFiles` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica uma lista de arquivos que controlam se uma recompilação é disparada quando a tarefa <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> é executada novamente, uma recompilação será acionada se um desses arquivos for alterado. |
| `GeneratedBamlFiles` | Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Contém a lista de arquivos gerados no formato binário XAML. |
| `GeneratedCodeFiles` | Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Contém a lista de arquivos de código gerenciado gerados. |
| `GeneratedLocalizationFiles` | Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Contém a lista de arquivos de localização que foram gerados para cada arquivo XAML localizado. |
| `HostInBrowser` | Parâmetro opcional **string.**<br /><br /> Especifica se o conjunto gerado é um XAML Browser Application (XBAP). As opções válidas são **true** e **false**. Se for **true**, código será gerado para dar suporte à hospedagem de navegador. |
| `KnownReferencePaths` | Parâmetro opcional **string[].**<br /><br /> Especifica as referências aos assemblies que não são alterados durante o processo de build. Inclui montagens localizadas no cache de montagem global (GAC), em um diretório de instalação .NET, e assim por diante. |
| `Language` | Parâmetro obrigatório **String**.<br /><br /> Especifica a linguagem gerenciada à qual o compilador dá suporte. As opções válidas são **C#**, **VB**, **JScript** e **C++**. |
| `LanguageSourceExtension` | Parâmetro opcional **string.**<br /><br /> Especifica a extensão que é acrescentada à extensão do arquivo de código gerenciado gerado:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Se o parâmetro **LanguageSourceExtension** não for definido com um valor específico, a extensão do nome do arquivo de origem padrão para um idioma será usada: *.vb* para Visual Basic, *.csharp* para C#. |
| `LocalizationDirectivesToLocFile` | Parâmetro opcional **string.**<br /><br /> Especifica como gerar informações de localização para cada arquivo XAML de origem. As opções válidas são **None**, **CommentsOnly** e **All**. |
| `OutputPath` | Parâmetro obrigatório **String**.<br /><br /> Especifica o diretório no qual os arquivos de código gerados e os arquivos de formato binário XAML são gerados. |
| `OutputType` | Parâmetro obrigatório **String**.<br /><br /> Especifica o tipo de assembly que é gerado por um projeto. As opções válidas são **winexe**, **exe**, **library** e **netmodule**. |
| `PageMarkup` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica uma lista de arquivos XAML para processar. |
| `References` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica a lista de referências de arquivos para conjuntos que contêm os tipos que são usados nos arquivos XAML. |
| `RequirePass2ForMainAssembly` | Parâmetro de saída opcional **Boolean**.<br /><br /> Indica se o projeto contém arquivos XAML não localizados que fazem referência a tipos locais incorporados no conjunto principal. |
| `RequirePass2ForSatelliteAssembly` | Parâmetro de saída opcional **Boolean**.<br /><br /> Indica se o projeto contém arquivos XAML localizados que fazem referência a tipos locais que estão incorporados no conjunto principal. |
| `RootNamespace` | Parâmetro opcional **string.**<br /><br /> Especifica o namespace raiz para as classes que estão dentro do projeto. **RootNamespace** também é usado como o namespace padrão de um arquivo de código `x:Class` gerenciado gerado quando o arquivo XAML correspondente não inclui o atributo. |
| `SourceCodeFiles` | Parâmetro **opcional ITaskItem[].**<br /><br /> Especifica a lista de arquivos de código para o projeto atual. A lista não inclui arquivos de código gerenciado específicos a um idioma gerados. |
| `UICulture` | Parâmetro opcional **string.**<br /><br /> Especifica o conjunto de satélites para a cultura de IA em que os arquivos de formato binário XAML gerados são incorporados. Se **o UICulture** não estiver definido, os arquivos de formato binário XAML gerados serão incorporados no conjunto principal. |
| `XAMLDebuggingInformation` | Parâmetro **booleano** opcional.<br /><br /> Quando **verdadeira,** as informações de diagnóstico são geradas e incluídas no XAML compilado para auxiliar na depuração. |

## <a name="remarks"></a>Comentários

A <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tarefa normalmente compila XAML em formato binário e gera arquivos de código. Se um arquivo XAML contiver referências a tipos definidos no mesmo projeto, sua compilação para o formato binário será adiada por **MarkupCompilePass1** para um segundo passe de compilação de marcação **(MarkupCompilePass2).** Esses arquivos devem ter sua compilação adiada porque eles devem aguardar até que os tipos referenciados definidos localmente sejam compilados. No entanto, se um `x:Class` arquivo <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> XAML tiver um atributo, gerará o arquivo de código específico do idioma para ele.

Um arquivo XAML é localizado se contiver elementos que usam o atributo: `x:Uid`

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Um arquivo XAML faz referência a um tipo definido localmente quando `clr-namespace` declara um namespace XML que usa o valor para se referir a um namespace no projeto atual:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Se qualquer arquivo XAML for localizado ou fizer referência a um tipo definido localmente, é necessário um segundo passe de compilação de marcação, o que requer a execução do [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) e, em seguida, o [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como converter três arquivos *XAML de página* em arquivos de formato binário. *Page1* contém uma referência a um tipo, `Class1`, que está no namespace raiz do projeto e, portanto, não é convertido em arquivos de formato binário nessa passagem de compilação de marcação. Em vez disso, o [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) é executado e é seguido de [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
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