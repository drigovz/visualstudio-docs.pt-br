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
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 4c7cc3490735dbd9ac43cd43555ec673cc3afccd
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070353"
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