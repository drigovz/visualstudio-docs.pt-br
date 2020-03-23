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
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631205"
---
# <a name="vcmessage-task"></a>tarefa VCMessage

Registra mensagens de aviso e erro durante o build.

## <a name="remarks"></a>Comentários

 Essa tarefa ajuda a implementar o MSBuild para projetos C++ e não se destina a ser chamada pelo usuário. Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **VCMessage**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**Argumentos**|Parâmetro opcional **string.**<br /><br /> Uma lista delimitada por ponto e vírgula de mensagens a serem exibidas.|
|**Código**|Parâmetro obrigatório **String**.<br /><br /> Um número de erro que qualifica a mensagem.|
|**Tipo**|Parâmetro opcional **string.**<br /><br /> Especifica o tipo de mensagem a ser emitida. Especifique "Warning" para emitir uma mensagem de aviso ou "Error" para emitir uma mensagem de erro.|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
