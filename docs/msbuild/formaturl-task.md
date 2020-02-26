---
title: Tarefa FormatUrl | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5d5a5d6cbe1f0e39f82d551c8c7933104110f4a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579660"
---
# <a name="formaturl-task"></a>Tarefa FormatUrl
Converte uma URL em um formato de URL correto.

## <a name="parameters"></a>parâmetros
 A tabela a seguir descreve os parâmetros da tarefa `FormatUrl`.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|`InputUrl`|Parâmetro `String` opcional.<br /><br /> Especifica a URL a ser formatada.|
|`OutputUrl`|Parâmetro de saída `String` opcional.<br /><br /> Especifica a URL formatada.|

## <a name="remarks"></a>Comentários
 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)