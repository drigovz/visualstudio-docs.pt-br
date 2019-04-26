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
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968055"
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