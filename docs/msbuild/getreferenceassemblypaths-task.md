---
title: Tarefa GetReferenceAssemblyPaths | Microsoft Docs
description: Use a tarefa MSBuild GetReferenceAssemblyPaths para retornar os caminhos do assembly de referência das várias estruturas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d3e0afdc7486e4337a92e3639c23c404050a84c4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914616"
---
# <a name="getreferenceassemblypaths-task"></a>Tarefa GetReferenceAssemblyPaths

Retorna os caminhos do assembly de referência de diversas estruturas.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `GetReferenceAssemblyPaths`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Parâmetro de saída `String[]` opcional.<br /><br /> Retorna o caminho com base no parâmetro `TargetFrameworkMoniker`. Se o `TargetFrameworkMoniker` for nulo ou vazio, esse caminho será `String.Empty`.|
|`FullFrameworkReferenceAssemblyPaths`|Parâmetro de saída `String[]` opcional.<br /><br /> Retorna o caminho com base no parâmetro `TargetFrameworkMoniker`, sem considerar a parte do perfil do moniker. Se o `TargetFrameworkMoniker` for nulo ou vazio, esse caminho será `String.Empty`.|
|`TargetFrameworkMoniker`|Parâmetro `String` opcional.<br /><br /> Especifica o moniker da estrutura de destino associada aos caminhos de assembly de referência.|
|`RootPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho raiz a ser usado para gerar o caminho do assembly de referência.|
|`BypassFrameworkInstallChecks`|Parâmetro <xref:System.Boolean> opcional.<br /><br /> Se `true`, ignora as verificações básicas que `GetReferenceAssemblyPaths` executa por padrão para garantir que determinadas estruturas de runtime sejam instaladas, dependendo da estrutura de destino.|
|`TargetFrameworkMonikerDisplayName`|Parâmetro de saída `String` opcional.<br /><br /> Especifica o nome de exibição do moniker da estrutura de destino.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)