---
title: Tarefa GetOutputFileName | Microsoft Docs
description: Use a tarefa auxiliar GetOutputFileName do MSBuild para especificar opções de nome de arquivo de saída para cl.exe e outras ferramentas.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436788"
---
# <a name="getoutputfilename-task"></a>Tarefa GetOutputFileName

Tarefa auxiliar para obter o nome do arquivo de saída para cl e outras ferramentas, que permite especificar somente o diretório de saída, o nome de arquivo completo ou nada.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutputFileName**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**OutputExtension**|Parâmetro de **cadeia de caracteres** necessário.|
|**OutputFile**|Parâmetro de saída de **cadeia de caracteres** opcional.|
|**OutputPath**|Parâmetro de **cadeia de caracteres** opcional.|
|**SourceFile**|Parâmetro de **cadeia de caracteres** necessário.|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)
