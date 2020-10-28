---
title: Tarefa CustomBuild | Microsoft Docs
description: Este artigo descreve a tarefa de CustomBuild do MSBuild, que é usada pelo MSBuild para dar suporte à personalização do processo de compilação do C++.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 640c1e6ae286b45f8700709829140093452a9491
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796544"
---
# <a name="custombuild-task"></a>Tarefa CustomBuild

Encapsula a ferramenta de compilador do Microsoft C++, cmd.exe. Essa classe deriva [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mas não usa o acompanhamento de arquivo para descobrir dependências de arquivo. Todas as dependências devem ser especificadas explicitamente como AdditionalDependencies para que o build incremental funcione corretamente.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa **CustomBuild** .

|Parâmetro|Descrição|
|---------------|-----------------|
|**BuildSuffix**|Parâmetro de **cadeia de caracteres** opcional.|
|**Fontes**|Parâmetro **ITaskItem []** necessário.|
|**TrackerLogDirectory**|Parâmetro de **cadeia de caracteres** opcional.|

## <a name="see-also"></a>Veja também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)
