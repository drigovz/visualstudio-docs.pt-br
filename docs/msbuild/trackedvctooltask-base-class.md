---
title: Classe TrackedVCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8a4272f7800e0532c0674fe7117e839cb16557d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594923"
---
# <a name="trackedvctooltask-base-class"></a>Classe base TrackedVCToolTask

Muitas tarefas são herdadas na classe <xref:Microsoft.Build.Utilities.Task> e na classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Essa classe adiciona vários parâmetros para as tarefas que derivam de [VCToolTask](../msbuild/vctooltask-base-class.md). Esses parâmetros são listados neste documento.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros das classes base **TrackedVCToolTask**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Parâmetro opcional **bool**.|
|**EnableExecuteTool**|Parâmetro opcional **bool**.|
|**ExcludedInputPaths**|Parâmetro **opcional ITaskItem[].**|
|**MinimalRebuildFromTracking**|Parâmetro opcional **bool**.|
|**PathOverride**|Parâmetro opcional **de string.**|
|**PostBuildTrackingCleanup**|Parâmetro opcional **bool**.|
|**RootSource**|Parâmetro opcional **de string.**|
|**SkippedExecution**|Parâmetro de saída **bool** opcional.|
|**SourcesCompiled**|Parâmetro de saída opcional **ITaskItem[]**.|
|**TLogCommandFile**|Parâmetro opcional **ITaskItem**.|
|**TLogReadFiles**|Parâmetro **opcional ITaskItem[].**|
|**TLogWriteFiles**|Parâmetro **opcional ITaskItem[].**|
|**ToolArchitecture**|Parâmetro opcional **de string.**|
|**TrackCommandLines**|Parâmetro opcional **bool**.|
|**TrackFileAccess**|Parâmetro opcional **bool**.|
|**TrackedInputFilesToIgnore**|Parâmetro **opcional ITaskItem[].**|
|**TrackedOutputFilesToIgnore**|Parâmetro **opcional ITaskItem[].**|
|**TrackerFrameworkPath**|Parâmetro opcional **de string.**|
|**TrackerSdkPath**|Parâmetro opcional **de string.**|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)<br/>
[Tarefas](../msbuild/msbuild-tasks.md)
