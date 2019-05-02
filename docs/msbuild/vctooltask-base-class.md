---
title: Classe VCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 7bdad856a6ea0ec6cca8292bc3095f51c500bcb1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970712"
---
# <a name="vctooltask-base-class"></a>Classe base VCToolTask

Muitas tarefas são herdadas na classe <xref:Microsoft.Build.Utilities.Task> e na classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Essa classe adiciona vários parâmetros para as tarefas que derivam dela. Esses parâmetros são listados neste documento.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros das classes base **VCToolTask**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Cadeia de caracteres opcional **Dictionary\<, parâmetro ToolSwitch>**.|
|**AdditionalOptions**|Parâmetro opcional **string**.|
|**EffectiveWorkingDirectory**|Parâmetro opcional **string**.|
|**EnableErrorListRegex**|Parâmetro opcional **bool**.<br/><br/>O padrão é `true`.|
|**ErrorListRegex**|Parâmetro opcional **ITaskItem[]**.|
|**ErrorListListExclusion**|Parâmetro opcional **ITaskItem[]**.|
|**GenerateCommandLine**|Parâmetro opcional **string**.<br/><br/>Usa valores **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parâmetro opcional **string**.<br/><br/>Usa valores **string[]** *switchesToRemove*, **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)<br/>
[Tarefas](../msbuild/msbuild-tasks.md)