---
title: Classe TrackedVCToolTask | Microsoft Docs
description: Saiba mais sobre os parâmetros que a classe base TrackedVCToolTask adiciona às tarefas que herdam dela.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046996"
---
# <a name="trackedvctooltask-base-class"></a>Classe base TrackedVCToolTask

Muitas tarefas são herdadas na classe <xref:Microsoft.Build.Utilities.Task> e na classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Essa classe adiciona vários parâmetros para as tarefas que derivam de [VCToolTask](../msbuild/vctooltask-base-class.md). Esses parâmetros são listados neste documento.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros das classes base **TrackedVCToolTask** .

|Parâmetro|Descrição|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Parâmetro opcional **bool** .|
|**EnableExecuteTool**|Parâmetro opcional **bool** .|
|**ExcludedInputPaths**|Parâmetro opcional **ITaskItem []** .|
|**MinimalRebuildFromTracking**|Parâmetro opcional **bool** .|
|**PathOverride**|Parâmetro de **cadeia de caracteres** opcional.|
|**PostBuildTrackingCleanup**|Parâmetro opcional **bool** .|
|**RootSource**|Parâmetro de **cadeia de caracteres** opcional.|
|**SkippedExecution**|Parâmetro de saída **bool** opcional.|
|**SourcesCompiled**|Parâmetro de saída opcional **ITaskItem[]** .|
|**TLogCommandFile**|Parâmetro opcional **ITaskItem** .|
|**TLogReadFiles**|Parâmetro opcional **ITaskItem []** .|
|**TLogWriteFiles**|Parâmetro opcional **ITaskItem []** .|
|**ToolArchitecture**|Parâmetro de **cadeia de caracteres** opcional.|
|**TrackCommandLines**|Parâmetro opcional **bool** .|
|**TrackFileAccess**|Parâmetro opcional **bool** .|
|**TrackedInputFilesToIgnore**|Parâmetro opcional **ITaskItem []** .|
|**TrackedOutputFilesToIgnore**|Parâmetro opcional **ITaskItem []** .|
|**TrackerFrameworkPath**|Parâmetro de **cadeia de caracteres** opcional.|
|**TrackerSdkPath**|Parâmetro de **cadeia de caracteres** opcional.|

## <a name="see-also"></a>Veja também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)<br/>
[Tarefas](../msbuild/msbuild-tasks.md)
