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
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593285"
---
# <a name="getoutputfilename-task"></a>Tarefa GetOutputFileName

Tarefa auxiliar para obter o nome do arquivo de saída para cl e outras ferramentas, que permite especificar somente o diretório de saída, o nome de arquivo completo ou nada.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutputFileName**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**OutputExtension**|Parâmetro obrigatório **string**.|
|**OutputFile**|Parâmetro de saída opcional **string**.|
|**OutputPath**|Parâmetro opcional **string**.|
|**SourceFile**|Parâmetro obrigatório **string**.|

## <a name="see-also"></a>Veja também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)
