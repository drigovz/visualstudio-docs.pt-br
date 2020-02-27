---
title: Tarefa RequiresFramework35SP1Assembly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: caefe0887ca23cd4cee60c3a4ba2a6133e9893df
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632765"
---
# <a name="requiresframework35sp1assembly-task"></a>Tarefa RequiresFramework35SP1Assembly

Determina se o aplicativo requer o .NET Framework 3.5 SP1.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `RequiresFramework35SP1Assembly`.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|`Assemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Define os assemblies referenciados no aplicativo.|
|`CreateDesktopShortcut`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, cria um ícone de atalho na área de trabalho durante a instalação.|
|`DeploymentManifestEntryPoint`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o nome do arquivo de manifesto para o aplicativo.|
|`EntryPoint`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o assembly que deve ser executado quando o aplicativo for executado.|
|`ErrorReportUrl`|Parâmetro `String` opcional.<br /><br /> Especifica o site que é exibido nas caixas de diálogo que são encontradas durante as instalações do ClickOnce.|
|`Files`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica a lista de arquivos que serão implantados quando o aplicativo for publicado.|
|`ReferencedAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Define os assemblies referenciados no projeto.|
|`RequiresMinimumFramework35SP1`|Parâmetro de saída `Boolean` opcional.<br /><br /> Se `true`, o aplicativo requer o .NET Framework 3.5 SP1.|
|`SigningManifests`|Parâmetro de saída `Boolean` opcional.<br /><br /> Se `true`, os manifestos do ClickOnce são assinados.|
|`SuiteName`|Parâmetro `String` opcional.<br /><br /> Especifica o nome da pasta no menu **Iniciar** no qual o aplicativo será instalado.|
|`TargetFrameworkVersion`|Parâmetro `String` opcional.<br /><br /> Especifica a versão do .NET Framework que o aplicativo direciona.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)