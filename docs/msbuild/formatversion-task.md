---
title: Tarefa FormatVersion | Microsoft Docs
description: Saiba mais sobre várias maneiras pelas quais as tarefas do MSBuild FormatVersion acrescentam o número de revisão ao número de versão.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6444811750a59de5488b8ca3614f9926d472746
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905479"
---
# <a name="formatversion-task"></a>Tarefa FormatVersion

Acrescenta o número de revisão ao número de versão.

- #1 de caso: entrada: versão = \<undefined> ;  Revisão = \<don't care> ;   Saída: OutputVersion = "1.0.0.0"

- Caso #2: Entrada: Version="1.0.0.*"  Revision="5"  Saída: OutputVersion="1.0.0.5"

- #3 de caso: entrada: versão = "1.0.0.0" revisão = \<don't care> ;  Saída: OutputVersion = "1.0.0.0"

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `FormatVersion`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`FormatType`|Parâmetro `String` opcional.<br /><br /> Especifica o tipo do formato.<br /><br /> -"Versão" = versão.<br />-   "Path" = substituir "." por "_";|
|`OutputVersion`|Parâmetro de saída `String` opcional.<br /><br /> Especifica a versão de saída que inclui o número de revisão.|
|`Revision`|Parâmetro `Int32` opcional.<br /><br /> Especifica a revisão a ser acrescentada à versão.|
|`Version`|Parâmetro `String` opcional.<br /><br /> Especifica a cadeia de caracteres do número de versão para o formato.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
