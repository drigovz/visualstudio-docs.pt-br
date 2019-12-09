---
title: Tarefa CPPClean | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d6e893dcf289c5060f519523b18b53b701f8055
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748119"
---
# <a name="cppclean-task"></a>Tarefa CPPClean
Exclui os arquivos temporários que o MSBuild cria C++ quando um projeto é compilado. O processo de exclusão de arquivos de build é conhecido como *limpeza*.

## <a name="parameters"></a>Parâmetros
 A tabela a seguir descreve os parâmetros da tarefa **CPPClean**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**DeletedFiles**|Parâmetro de saída `ITaskItem[]` opcional.<br /><br /> Define uma matriz de itens de arquivo de saída do MSBuild que pode ser consumida e emitida por tarefas.|
|**DoDelete**|Parâmetro **Boolean** opcional.<br /><br /> Se `true`, limpará arquivos de build temporários.|
|**FilePatternsToDeleteOnClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de extensões de arquivo dos arquivos a serem limpos.|
|**FilesExcludedFromClean**|Parâmetro `String` opcional.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de arquivos que não serão limpos.|
|**FoldersToClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de diretórios a serem limpos. É possível especificar um caminho completo ou relativo e esse caminho pode conter o símbolo curinga (*).|

## <a name="see-also"></a>Consulte também
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)