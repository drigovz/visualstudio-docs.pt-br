---
title: Tarefa SetEnv | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49d25d49554c587bcaaba8ef09bac967d4b5599a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660665"
---
# <a name="setenv-task"></a>Tarefa SetEnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define ou exclui o valor de uma variável de ambiente especificada.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **SetEnv**.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**Nome**|Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> O nome de uma variável de ambiente.|  
|**OutputEnvironmentVariable**|Parâmetro de saída opcional **String**.<br /><br /> Contém o valor atribuído à variável de ambiente especificado pelo parâmetro **Nome**.|  
|**Prefixo**|Parâmetro `Boolean` obrigatório.<br /><br /> Se `true`, concatenará o valor do parâmetro **Valor** antes do valor da variável de ambiente especificado pelo parâmetro **Nome** e, em seguida, atribuirá o resultado à variável de ambiente. Se `false`, atribuirá somente o valor do parâmetro **Valor** à variável de ambiente.|  
|**Target**|Parâmetro **String** opcional.<br /><br /> Especifica o local em que uma variável de ambiente é armazenada. Especifique "`User`" ou "`Machine`".<br /><br /> Para obter mais informações, consulte "Enumeração EnvironmentVariableTarget" no site do [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Valor**|Parâmetro **String** opcional.<br /><br /> O valor atribuído à variável de ambiente especificado pelo parâmetro **Nome**. Se **Valor** estiver vazio e a variável existir, a variável será excluída. Se a variável não existir, nenhum erro ocorrerá mesmo que a operação não possa ser executada.<br /><br /> Para obter mais informações, consulte "Environment::SetEnvironmentVariable Method" no site do [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
