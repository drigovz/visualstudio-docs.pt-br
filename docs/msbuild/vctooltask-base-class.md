---
title: Classe VCToolTask | Microsoft Docs
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
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591665"
---
# <a name="vctooltask-base-class"></a>Classe base VCToolTask

Muitas tarefas são herdadas na classe <xref:Microsoft.Build.Utilities.Task> e na classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Essa classe adiciona vários parâmetros para as tarefas que derivam dela. Esses parâmetros são listados neste documento.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros das classes base **VCToolTask**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Cadeia de caracteres opcional **Dictionary\<, parâmetro ToolSwitch>**.|
|**AdditionalOptions**|Parâmetro opcional **de string.**|
|**EffectiveWorkingDirectory**|Parâmetro opcional **de string.**|
|**EnableErrorListRegex**|Parâmetro opcional **bool**.<br/><br/>O padrão é `true`.|
|**ErrorListRegex**|Parâmetro **opcional ITaskItem[].**|
|**ErrorListListExclusion**|Parâmetro **opcional ITaskItem[].**|
|**GenerateCommandLine**|Parâmetro opcional **de string.**<br/><br/>Usa valores **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parâmetro opcional **de string.**<br/><br/>Usa valores **string[]** *switchesToRemove*, **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)<br/>
[Tarefas](../msbuild/msbuild-tasks.md)
