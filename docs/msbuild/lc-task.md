---
title: Tarefa LC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86525b2c4ddcf36ca85feee31f89f0003f1f9775
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590820"
---
# <a name="lc-task"></a>tarefa LC
Encapsula *LC.exe*, que gera um arquivo *.license* com base em um arquivo *.licx*. Para obter mais informações sobre *LC.exe*, confira [Lc.exe (Compilador de Licença)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parâmetros
A tabela a seguir descreve os parâmetros da tarefa `LC`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`LicenseTarget`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o executável para o qual os arquivos *.licenses* são gerados.|
|`NoLogo`|Parâmetro `Boolean` opcional.<br /><br /> Suprime a exibição do banner de inicialização da Microsoft.|
|`OutputDirectory`|Parâmetro `String` opcional.<br /><br /> Especifica o diretório no qual colocar os arquivos *.licenses* de saída.|
|`OutputLicense`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o nome do arquivo *.licenses*. Se você não especificar um nome, o nome do arquivo *.licx* será usado e o arquivo *.licenses* será colocado no diretório que contém o arquivo *.licx*.|
|`ReferencedAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os componentes referenciados a serem carregados ao gerar o arquivo *.license*.|
|`SdkToolsPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho para o SDK Tools, como *resgen.exe*.|
|`Sources`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os itens que contêm os componentes licenciados a serem incluídos no arquivo *.licenses*. Para obter mais informações, consulte a documentação da opção `/complist` em [Lc.exe (Compilador de Licença)](/dotnet/framework/tools/lc-exe-license-compiler).|

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.ToolTask>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Exemplo
O exemplo a seguir usa a tarefa `LC` para compilar licenças.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Veja também
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
