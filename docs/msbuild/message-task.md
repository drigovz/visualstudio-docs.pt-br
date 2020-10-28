---
title: Tarefa de mensagem | Microsoft Docs
description: Saiba mais sobre os parâmetros e as configurações da tarefa de mensagem do MSBuild, que registra as mensagens durante as compilações.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1b7a2854220a7ee85fd680cedd8c8e0c5c3ada89
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903837"
---
# <a name="message-task"></a>tarefa de mensagem

Registra uma mensagem durante a compilação.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `Message`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Importance`|Parâmetro `String` opcional.<br /><br /> Especifica a importância da mensagem. Esse parâmetro pode ter um valor igual a `high`, `normal` ou `low`. O valor padrão é `normal`.|
|`Text`|Parâmetro `String` opcional.<br /><br /> O texto de erro do log.|

## <a name="remarks"></a>Comentários

 A `Message` tarefa permite que os projetos do MSBuild emitam mensagens para os agentes em diferentes etapas no processo de compilação.

 Se o parâmetro `Condition` avaliar para o `true`, o valor do parâmetro `Text` será registrado e a compilação dará continuidade à execução. Se um parâmetro `Condition` não existir, o texto da mensagem será registrado. Para saber mais sobre o log, confira [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md).

 Por padrão, a mensagem é enviada a todos os agentes de log registrados. O agente de log interpreta o parâmetro `Importance`. Normalmente, uma mensagem definida como `high` é enviada quando o detalhe do agente é definido como <xref:Microsoft.Build.Framework.LoggerVerbosity> .`Minimal` ou posterior. Uma mensagem definida como `low` é enviada quando o detalhe do agente é definido como <xref:Microsoft.Build.Framework.LoggerVerbosity> . `Detailed` .

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

## <a name="see-also"></a>Veja também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Obter logs de build](../msbuild/obtaining-build-logs-with-msbuild.md)
