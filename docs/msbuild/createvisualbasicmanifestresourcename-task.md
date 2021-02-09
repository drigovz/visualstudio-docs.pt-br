---
title: Tarefa CreateVisualBasicManifestResourceName | Microsoft Docs
description: Use a tarefa MSBuild CreateVisualBasicManifestResourceName para criar um nome de manifesto estilo Visual Basic de um determinado nome de arquivo. resx ou outro recurso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CreateVisualBasicManifestResourceName task
- CreateVisualBasicManifestResourceName task [MSBuild]
ms.assetid: 251c47b9-de32-414b-a138-bf45290af12e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8e9f0868cb774ee82c79ba190acddebf63193cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901380"
---
# <a name="createvisualbasicmanifestresourcename-task"></a>Tarefa CreateVisualBasicManifestResourceName

Cria um nome de manifesto estilo Visual Basic a partir de um determinado nome de arquivo *. resx* ou outro recurso.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da [tarefa CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md).

| Parâmetro | Descrição |
| - | - |
| `ManifestResourceNames` | <xref:Microsoft.Build.Framework.ITaskItem>`[]`parâmetro somente leitura de saída.<br /><br /> Os nomes de manifesto resultantes. |
| `ResourceFiles` | Parâmetro `String` obrigatório.<br /><br /> O nome do arquivo de recurso do qual criar o nome do manifesto do Visual Basic. |
| `RootNamespace` | Parâmetro `String` opcional.<br /><br /> O namespace raiz do arquivo de recurso, geralmente obtido do arquivo de projeto. Pode ser `null`. |
| `PrependCultureAsDirectory` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, o nome da cultura é adicionado como um nome de diretório antes do nome do recurso de manifesto. O valor padrão é `true`. |
| `ResourceFilesWithManifestResourceNames` | Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o nome do arquivo de recurso que agora inclui o nome do recurso de manifesto. |

## <a name="remarks"></a>Comentários

 A [tarefa CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md) determina o nome do recurso de manifesto apropriado a ser atribuído a um determinado arquivo *. resx* ou outro recurso. A tarefa fornece um nome lógico para um arquivo de recurso e, em seguida, anexa-o a um parâmetro de saída como metadados.

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Consulte também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
