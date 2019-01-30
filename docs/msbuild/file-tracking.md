---
title: Acompanhamento de arquivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 878d4d7e56c51d8a41a0e3cf3e78d6c83ed5d0b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027666"
---
# <a name="file-tracking"></a>Acompanhamento de arquivos
O acompanhamento de arquivo registra chamadas no sistema de arquivos do Windows para um processo e seus processos filho. Ao chamar as funções listadas abaixo, os programas controlam quando ativar e desativar esse registro e especificar o arquivo de log a ser usado.  
  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Para o acompanhamento no contexto atual.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Retomar acompanhamento após uma chamada para [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Definir o número de threads a serem usados para acompanhamento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Iniciar um novo contexto de acompanhamento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Iniciar um novo contexto de acompanhamento com uma raiz especificada.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Finalizar acompanhamento e recursos da versão usados.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Suspender temporariamente o acompanhamento.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Gravar os logs de acompanhamento para todos os contextos.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Gravar os logs de acompanhamento para o contexto atual.