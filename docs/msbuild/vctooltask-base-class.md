---
title: Classe VCToolTask | Microsoft Docs
description: Saiba mais sobre vários parâmetros que a classe base VCToolTask adiciona às tarefas que herdam dela.
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
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046740"
---
# <a name="vctooltask-base-class"></a>Classe base VCToolTask

Muitas tarefas são herdadas na classe <xref:Microsoft.Build.Utilities.Task> e na classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Essa classe adiciona vários parâmetros para as tarefas que derivam dela. Esses parâmetros são listados neste documento.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros das classes base **VCToolTask** .

|Parâmetro|Descrição|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Parâmetro **de \<string, ToolSwitch> dicionário** opcional.|
|**AdditionalOptions**|Parâmetro de **cadeia de caracteres** opcional.|
|**EffectiveWorkingDirectory**|Parâmetro de **cadeia de caracteres** opcional.|
|**EnableErrorListRegex**|Parâmetro opcional **bool** .<br/><br/>O padrão é `true`.|
|**ErrorListRegex**|Parâmetro opcional **ITaskItem []** .|
|**ErrorListListExclusion**|Parâmetro opcional **ITaskItem []** .|
|**GenerateCommandLine**|Parâmetro de **cadeia de caracteres** opcional.<br/><br/>Usa valores **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parâmetro de **cadeia de caracteres** opcional.<br/><br/>Usa valores **string[]** *switchesToRemove* , **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] e **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Veja também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)<br/>
[Tarefas](../msbuild/msbuild-tasks.md)
