---
title: Tarefa CPPClean | Microsoft Docs
description: Este artigo descreve a Tarefa CPPClean, que é usada para excluir os arquivos temporários que o MSBuild cria quando um projeto C++ é compilado.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5b3d48c4556cfd05e5ce3f2b893b3f0e9a07226
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901437"
---
# <a name="cppclean-task"></a>Tarefa CPPClean

Exclui os arquivos temporários que o MSBuild cria quando um projeto C++ é compilado. O processo de exclusão de arquivos de build é conhecido como *limpeza*.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **CPPClean**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**DeletedFiles**|Parâmetro de saída `ITaskItem[]` opcional.<br /><br /> Define uma matriz de itens de arquivo de saída do MSBuild que pode ser consumida e emitida por tarefas.|
|**DoDelete**|Parâmetro **booliano** opcional.<br /><br /> Se `true`, limpará arquivos de build temporários.|
|**FilePatternsToDeleteOnClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de extensões de arquivo dos arquivos a serem limpos.|
|**FilesExcludedFromClean**|Parâmetro `String` opcional.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de arquivos que não serão limpos.|
|**FoldersToClean**|Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de diretórios a serem limpos. É possível especificar um caminho completo ou relativo e esse caminho pode conter o símbolo curinga (*).|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
