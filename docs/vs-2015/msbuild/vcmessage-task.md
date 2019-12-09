---
title: Tarefa VCMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 508d1fe33046f6051c9c5c1b8e54036e78ae7d2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193346"
---
# <a name="vcmessage-task"></a>Tarefa VCMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Registra mensagens de aviso e erro durante o build.  
  
## <a name="remarks"></a>Comentários  
 Essa tarefa ajuda a implementar o MSBuild para o Visual C++ e não se destina a ser chamada pelo usuário. Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **VCMessage**.  
  
|Parâmetro|DESCRIÇÃO|  
|---------------|-----------------|  
|**Argumentos**|Parâmetro **String** opcional.<br /><br /> Uma lista delimitada por ponto e vírgula de mensagens a serem exibidas.|  
|**Código**|Parâmetro da **cadeia de caracteres** obrigatório.<br /><br /> Um número de erro que qualifica a mensagem.|  
|**Tipo**|Parâmetro **String** opcional.<br /><br /> Especifica o tipo de mensagem a ser emitida. Especifique `"Warning"` para emitir uma mensagem de aviso ou `"Error"` para emitir uma mensagem de erro.|  
  
## <a name="see-also"></a>Veja também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
