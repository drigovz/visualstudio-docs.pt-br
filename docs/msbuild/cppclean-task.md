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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 331a96c7cd67b933e521e3fe5f2d7a909ffa5d03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634338"
---
# <a name="cppclean-task"></a>Tarefa CPPClean

Exclui os arquivos temporários que o MSBuild cria quando um projeto C++ é construído. O processo de exclusão de arquivos de build é conhecido como *limpeza*.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **CPPClean**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**DeletedFiles**|Parâmetro de saída `ITaskItem[]` opcional.<br /><br /> Define uma matriz de itens de arquivo de saída do MSBuild que pode ser consumida e emitida por tarefas.|
|**DoDelete**|Parâmetro **booleano** opcional.<br /><br /> Se `true`, limpará arquivos de build temporários.|
|**FilePatternsToDeleteOnClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de extensões de arquivo dos arquivos a serem limpos.|
|**FilesExcludedFromClean**|Parâmetro `String` opcional.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de arquivos que não serão limpos.|
|**FoldersToClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de diretórios a serem limpos. É possível especificar um caminho completo ou relativo e esse caminho pode conter o símbolo curinga (*).|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
