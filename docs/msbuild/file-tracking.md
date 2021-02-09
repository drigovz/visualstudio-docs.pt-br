---
title: Acompanhamento de arquivos | Microsoft Docs
description: Use funções de rastreamento de arquivo do MSBuild para registrar chamadas para o sistema de arquivos do Windows para um processo e seus processos filho.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877116"
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
