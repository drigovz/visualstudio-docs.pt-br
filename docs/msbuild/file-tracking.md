---
title: Acompanhamento de arquivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9335ca6608d36edbd17e47a441e13aecaa41c890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634195"
---
# <a name="file-tracking"></a>Acompanhamento de arquivos

O acompanhamento de arquivo registra chamadas no sistema de arquivos do Windows para um processo e seus processos filho. Ao chamar as funções listadas abaixo, os programas controlam quando ativar e desativar esse registro e especificar o arquivo de log a ser usado.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Interrompa o acompanhamento do contexto atual.

- [ResumeTracking](../msbuild/resumetracking.md) Retome o acompanhamento após uma chamada a [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Defina o número de threads a serem usados para acompanhamento.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Inicie um novo contexto de acompanhamento.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Inicie um novo contexto de acompanhamento com uma raiz especificada.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Encerre os recursos acompanhamento e de versão usados.

- [SuspendTracking](../msbuild/suspendtracking.md) Suspenda temporariamente o acompanhamento.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Grave os logs de acompanhamento para todos os contextos.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Grave os logs de acompanhamento para o contexto atual.
