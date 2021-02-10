---
title: Classe base Task | Microsoft Docs
description: Saiba mais sobre os parâmetros que a classe base Microsoft. Build. Utilities. Task adiciona às tarefas que herdam dela.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf6bc7cf353a8a1da7854a350f352e69013eb52e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966091"
---
# <a name="task-base-class"></a>Classe base Task

Muitas tarefas são herdadas da classe <xref:Microsoft.Build.Utilities.Task>. Essa classe adiciona vários parâmetros para as tarefas que derivam dela. Esses parâmetros são listados neste documento.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros dessa classe base.

|Parâmetro|Descrição|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica a interface de mecanismo de compilação disponível para tarefas. O mecanismo de compilação define automaticamente esse parâmetro para permitir que tarefas retornem para ele.<br /><br /> Esta é uma propriedade de conveniência para que os autores de tarefa que herdam desta classe não precisem converter o valor de `IBuildEngine` para `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parâmetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica a interface de mecanismo de build disponível para tarefas.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parâmetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica a instância do objeto de host (pode ser nulo). O mecanismo de compilação define essa propriedade se o IDE do host associou um objeto de host com essa tarefa em particular.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Parâmetro <xref:Microsoft.Build.Utilities.TaskLoggingHelper> somente leitura opcional.<br /><br /> O objeto auxiliar de registro em log.|

## <a name="see-also"></a>Consulte também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
