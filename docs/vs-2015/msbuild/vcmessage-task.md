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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193346"
---
# <a name="vcmessage-task"></a>Tarefa VCMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Registra mensagens de aviso e erro durante o build.  
  
## <a name="remarks"></a>Comentários  
 Essa tarefa ajuda a implementar o MSBuild para o Visual C++ e não se destina a ser chamada pelo usuário. Para obter mais informações, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **VCMessage**.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|**Argumentos**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Uma lista delimitada por ponto e vírgula de mensagens a serem exibidas.|  
|**Código**|Parâmetro obrigatório **String**.<br /><br /> Um número de erro que qualifica a mensagem.|  
|**Tipo**|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica o tipo de mensagem a ser emitida. Especifique `"Warning"` para emitir uma mensagem de aviso ou `"Error"` para emitir uma mensagem de erro.|  
  
## <a name="see-also"></a>Consulte Também  
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)
