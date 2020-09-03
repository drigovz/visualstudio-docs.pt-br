---
title: Tarefa CPPClean | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bddba1170cf675b5bde7ab8deed8cce1e7eb57dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196572"
---
# <a name="cppclean-task"></a>Tarefa CPPClean
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Exclui os arquivos temporários que o MSBuild cria quando um projeto Visual C++ é criado. O processo de exclusão de arquivos de build é conhecido como *limpeza*.  

## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **CPPClean**.  

|            Parâmetro            |                                                                                                Descrição                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Parâmetro de saída `ITaskItem[]` opcional.<br /><br /> Define uma matriz de itens de arquivo de saída do MSBuild que pode ser consumida e emitida por tarefas.                                |
|          **DoDelete**           |                                                            Parâmetro **booliano** opcional.<br /><br /> Se `true`, limpará arquivos de build temporários.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de extensões de arquivo dos arquivos a serem limpos.                                             |
|   **FilesExcludedFromClean**    |                                                    Parâmetro `String` opcional.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de arquivos que não serão limpos.                                                    |
|       **FoldersToClean**        | Parâmetro `String` obrigatório.<br /><br /> Especifica uma lista delimitada por ponto e vírgula de diretórios a serem limpos. Você pode especificar um caminho completo ou relativo, e o caminho pode conter o símbolo curinga ( **\\** \* ). |

## <a name="remarks"></a>Comentários  

## <a name="see-also"></a>Consulte Também  
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)
