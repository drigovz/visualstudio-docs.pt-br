---
title: Tarefa ResolveManifestFiles | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa ResolveManifestFiles para resolver itens no processo de compilação para arquivos para geração de manifesto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b67483c82e19c51da776d6ec40066ba5223a238a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912517"
---
# <a name="resolvemanifestfiles-task"></a>Tarefa ResolveManifestFiles

Resolve os seguintes itens no processo de build para arquivos de geração de manifesto: itens compilados, dependências, satélites, conteúdo, símbolos de depuração e documentação.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `ResolveManifestFiles`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`DeploymentManifestEntryPoint`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o nome do manifesto de implantação.|
|`EntryPoint`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o assembly gerenciado ou a referência do manifesto do ClickOnce que é o ponto de entrada para o manifesto.|
|`ExtraFiles`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos extras.|
|`ManagedAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os assemblies gerenciados.|
|`NativeAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os assemblies nativos.|
|`OutputAssemblies`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica os assemblies gerados.|
|`OutputDeploymentManifestEntryPoint`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o ponto de entrada do manifesto de implantação de saída.|
|`OutputEntryPoint`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o ponto de entrada de saída.|
|`OutputFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica os arquivos de saída.|
|`PublishFiles`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos de publicação.|
|`SatelliteAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> especifica os assemblies satélite.|
|`SigningManifests`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, os manifestos são assinados.|
|`TargetCulture`|Parâmetro `String` opcional.<br /><br /> Especifica a cultura de destino para assemblies satélite.|
|`TargetFrameworkVersion`|Parâmetro `String` opcional.<br /><br /> Especifica a versão do .NET Framework de destino.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
