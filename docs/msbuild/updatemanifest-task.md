---
title: Tarefa UpdateManifest | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa UpdateManifest para atualizar as propriedades selecionadas em um manifesto e desistir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fab3844b21e12edceb83da310e9069199578ef6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046851"
---
# <a name="updatemanifest-task"></a>Tarefa UpdateManifest

Atualiza as propriedades selecionadas em um manifesto e assina-as novamente.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `UpdateManifest`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`ApplicationManifest`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o manifesto do aplicativo.|
|`ApplicationPath`|Parâmetro `String` obrigatório.<br /><br /> Especifica o caminho do manifesto do aplicativo.|
|`InputManifest`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o manifesto a atualizar.|
|`OutputManifest`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o manifesto que contém propriedades atualizadas.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados na tabela, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [classe base da tarefa](../msbuild/task-base-class.md).

## <a name="see-also"></a>Veja também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)