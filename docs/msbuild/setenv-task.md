---
title: Tarefa SetEnv | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa SetEnv para definir ou excluir o valor de uma variável de ambiente especificada.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- SetEnv task (MSBuild (C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 76fc0d0dafac542ffde8656c643ec01b7ce23a39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861667"
---
# <a name="setenv-task"></a>Tarefa SetEnv

Define ou exclui o valor de uma variável de ambiente especificada.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa **SetEnv**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**Nome**|Parâmetro obrigatório **String**.<br /><br /> O nome de uma variável de ambiente.|
|**OutputEnvironmentVariable**|Parâmetro de saída opcional **String**.<br /><br /> Contém o valor atribuído à variável de ambiente especificado pelo parâmetro **Nome**.|
|**Prefix**|Parâmetro `Boolean` obrigatório.<br /><br /> Se `true`, concatenará o valor do parâmetro **Valor** antes do valor da variável de ambiente especificado pelo parâmetro **Nome** e, em seguida, atribuirá o resultado à variável de ambiente. Se `false`, atribuirá somente o valor do parâmetro **Valor** à variável de ambiente.|
|**Target (destino)**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o local em que uma variável de ambiente é armazenada. Especifique "User" ou "Machine".<br /><br /> Para saber mais, confira [Enumeração EnvironmentVariableTarget](xref:System.EnvironmentVariableTarget).|
|**Valor**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> O valor atribuído à variável de ambiente especificado pelo parâmetro **Nome**. Se **Valor** estiver vazio e a variável existir, a variável será excluída. Se a variável não existir, nenhum erro ocorrerá mesmo que a operação não possa ser executada.<br /><br /> Para saber mais, confira [Método Environment::SetEnvironmentVariable](xref:System.Environment.SetEnvironmentVariable%2A).|

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
