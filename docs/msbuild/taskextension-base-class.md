---
title: Classe Base TaskExtension | Microsoft Docs
description: Saiba mais sobre os parâmetros que a classe base Microsoft. Build. Tasks. TaskExtension adiciona às tarefas que herdam dela.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6692cb16b3861d72bf713c22b2ecfb2ee95bc036
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965974"
---
# <a name="taskextension-base-class"></a>Classe base TaskExtension

Muitas tarefas são herdadas da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que é herdada da classe <xref:Microsoft.Build.Utilities.Task>. Esta cadeia de herança adiciona vários parâmetros nas tarefas que derivam deles. Esses parâmetros são listados neste documento.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros das classes base.

|Parâmetro|Descrição|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.<br /><br /> Esta é uma propriedade de conveniência para que os autores de tarefa que herdam desta classe não precisem converter o valor de `IBuildEngine` para `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica a interface de mecanismo de build disponível para tarefas.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parâmetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica a instância do objeto de host (pode ser nulo). O mecanismo de compilação define essa propriedade se o IDE do host associou um objeto de host com essa tarefa em particular.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Parâmetro <xref:Microsoft.Build.Utilities.TaskLoggingHelper> somente leitura opcional.<br /><br /> Obtém um objeto `TaskLoggingHelperExtension` que contém os métodos de registro de tarefa.|

## <a name="see-also"></a>Consulte também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
