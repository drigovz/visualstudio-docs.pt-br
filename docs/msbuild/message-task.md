---
title: Tarefa de mensagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865356"
---
# <a name="message-task"></a>tarefa de mensagem

Registra uma mensagem durante a compilação.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `Message`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Importance`|Parâmetro `String` opcional.<br /><br /> Especifica a importância da mensagem. Esse parâmetro pode ter um valor igual a `high`, `normal` ou `low`. O valor padrão é `normal`.|
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto de erro do log.|

## <a name="remarks"></a>Comentários

 A `Message` tarefa permite que projetos do MSBuild emitam mensagens para madeireiros em diferentes etapas do processo de compilação.

 Se o parâmetro `Condition` avaliar para o `true`, o valor do parâmetro `Text` será registrado e a compilação dará continuidade à execução. Se um parâmetro `Condition` não existir, o texto da mensagem será registrado. Para saber mais sobre o log, confira [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).

 Por padrão, a mensagem é enviada a todos os madeireiros registrados. O agente de log interpreta o parâmetro `Importance`. Normalmente, uma mensagem definida para `high` é enviada quando <xref:Microsoft.Build.Framework.LoggerVerbosity>a verbosidade do logger é definida como .`Minimal` ou posterior. Uma mensagem `low` definida para é enviada quando a <xref:Microsoft.Build.Framework.LoggerVerbosity>verbosidade do logger é definida como . `Detailed`.

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo de código a seguir registra mensagens para todos os agentes de log registrados.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md)
