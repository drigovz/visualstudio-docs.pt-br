---
title: Tarefa VCMessage | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa VCMessage para registrar mensagens de aviso e de erro durante uma compilação para projetos C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046747"
---
# <a name="vcmessage-task"></a>tarefa VCMessage

Registra mensagens de aviso e erro durante o build.

## <a name="remarks"></a>Comentários

 Essa tarefa ajuda a implementar o MSBuild para projetos C++ e não se destina a ser chamado pelo usuário. Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **VCMessage** .

|Parâmetro|Descrição|
|---------------|-----------------|
|**Argumentos**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Uma lista delimitada por ponto e vírgula de mensagens a serem exibidas.|
|**Código**|Parâmetro obrigatório **String** .<br /><br /> Um número de erro que qualifica a mensagem.|
|**Tipo**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o tipo de mensagem a ser emitida. Especifique "Warning" para emitir uma mensagem de aviso ou "Error" para emitir uma mensagem de erro.|

## <a name="see-also"></a>Veja também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
