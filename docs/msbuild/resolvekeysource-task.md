---
title: Tarefa ResolveKeySource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0902bb891d044ab5ad2c657a73f363d8df9e601e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986928"
---
# <a name="resolvekeysource-task"></a>Tarefa ResolveKeySource
Determina a origem da chave de nome forte.  
  
## <a name="task-parameters"></a>Parâmetros de tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `ResolveKeySource`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Parâmetro `Int32` opcional.<br /><br /> Obtém ou define a quantidade de tempo, em segundos, para exibir a contagem de mensagem de inatividade.|  
|`AutoClosePasswordPromptTimeout`|Parâmetro `Int32` opcional.<br /><br /> Obtém ou define o período de tempo, em segundos, a esperar antes de fechar a caixa de diálogo de aviso de senha.|  
|`CertificateFile`|Parâmetro `String` opcional.<br /><br /> Obtém ou define o caminho do arquivo do certificado.|  
|`CertificateThumbprint`|Parâmetro `String` opcional.<br /><br /> Obtém ou define a impressão digital do certificado.|  
|`KeyFile`|Parâmetro `String` opcional.<br /><br /> Obtém ou define o caminho do arquivo da chave.|  
|`ResolvedKeyContainer`|Parâmetro de saída `String` opcional.<br /><br /> Obtém ou define o contêiner de chave resolvido.|  
|`ResolvedKeyFile`|Parâmetro de saída `String` opcional.<br /><br /> Obtém ou define o contêiner de arquivo resolvido.|  
|`ResolvedThumbprint`|Parâmetro de saída `String` opcional.<br /><br /> Obtém ou define a impressão digital do certificado resolvido.|  
|`ShowImportDialogDespitePreviousFailures`|Parâmetro `Boolean` opcional.<br /><br /> Se `true`, mostra a caixa de diálogo Importar apesar das falhas anteriores.|  
|`SuppressAutoClosePasswordPrompt`|Parâmetro `Boolean` opcional.<br /><br /> Obtém ou define um valor booliano que especifica se a caixa de diálogo de aviso de senha deve não fechamento automático.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)