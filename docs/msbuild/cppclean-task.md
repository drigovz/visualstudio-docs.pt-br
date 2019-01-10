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
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbf575db0289f0b5bbb5fbcd0bf47605871e52c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966366"
---
# <a name="cppclean-task"></a>Tarefa CPPClean
Exclui os arquivos temporários criados pelo MSBuild quando projeto do Visual C++ é compilado. O processo de exclusão de arquivos de build é conhecido como *limpeza*.  
  
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
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)