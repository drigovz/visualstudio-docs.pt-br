---
title: Tarefa ResolveNativeReference| Microsoft Docs
description: Saiba como o MSBuild usa a tarefa ResolveNativeReference para resolver referências nativas implementando a classe Microsoft. Build. Tasks. ResolveNativeReference.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cb987ec458e91c4190e2e0c264a80592f8133e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912465"
---
# <a name="resolvenativereference-task"></a>Tarefa ResolveNativeReference

Resolve referências nativas. Implementa a classe <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Essa classe dá suporte à infraestrutura do .NET Framework, que não se destina a ser usada diretamente do seu código.

## <a name="task-parameters"></a>Parâmetros de tarefa

 A tabela a seguir descreve os parâmetros da tarefa `ResolveNativeReference`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`AdditionalSearchPaths`|Parâmetro <xref:System.String?displayProperty=fullName>`[]` obrigatório.<br /><br /> Obtém ou define os caminhos de pesquisa para resolver as identidades de assembly de referências nativas.|
|`ContainedComComponents`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os componentes COM do assembly nativo.|
|`ContainedLooseEtcFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os arquivos flexíveis, *etc* . listados no manifesto nativo.|
|`ContainedLooseTlbFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os arquivos *. tlb* soltos do assembly nativo.|
|`ContainedPrerequisiteAssemblies`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os assemblies que devem estar presentes antes que o manifesto possa ser usado.|
|`ContainedTypeLibraries`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define as bibliotecas de tipo do assembly nativo.|
|`ContainingReferenceFiles`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtém ou define os arquivos de referência.|
|`NativeReferences`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Obtém ou define as referências de assembly nativo do Win32.|

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
