---
title: Tarefa GetOutputFileName | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6298a512a1848622bf854d6d9ee9084309a0b4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977111"
---
# <a name="getoutputfilename-task"></a>Tarefa GetOutputFileName

Tarefa auxiliar para obter o nome do arquivo de saída para cl e outras ferramentas, que permite especificar somente o diretório de saída, o nome de arquivo completo ou nada.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutputFileName**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**OutputExtension**|Parâmetro obrigatório **string**.|
|**OutputFile**|Parâmetro de saída opcional **string**.|
|**OutputPath**|Parâmetro **string** opcional.|
|**SourceFile**|Parâmetro obrigatório **string**.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)