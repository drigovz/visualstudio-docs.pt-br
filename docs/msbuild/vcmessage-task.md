---
title: Tarefa VCMessage | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b1bf1eb222d70c18bfb94c65dddd2903864c68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591106"
---
# <a name="vcmessage-task"></a>tarefa VCMessage
Registra mensagens de aviso e erro durante o build.

## <a name="remarks"></a>Comentários
 Essa tarefa ajuda a implementar o C++ MSBuild para projetos e não se destina a ser chamada pelo usuário. Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parâmetros
 A tabela a seguir descreve os parâmetros da tarefa **VCMessage**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**Argumentos**|Parâmetro **String** opcional.<br /><br /> Uma lista delimitada por ponto e vírgula de mensagens a serem exibidas.|
|**Código**|Parâmetro obrigatório **String**.<br /><br /> Um número de erro que qualifica a mensagem.|
|**Tipo**|Parâmetro **String** opcional.<br /><br /> Especifica o tipo de mensagem a ser emitida. Especifique "Warning" para emitir uma mensagem de aviso ou "Error" para emitir uma mensagem de erro.|

## <a name="see-also"></a>Veja também
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
