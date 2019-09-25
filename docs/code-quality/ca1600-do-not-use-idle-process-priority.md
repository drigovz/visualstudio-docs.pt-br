---
title: 'CA1600: Não usar prioridade de processo ociosa'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 686929471ee8b6b5d1896f61bcbcd97a59135462
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234373"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Não usar prioridade de processo ociosa

|||
|-|-|
|NomeDoTipo|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Categoria|Microsoft.Mobility|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Essa regra ocorre quando os processos são definidos `ProcessPriorityClass.Idle`como.

## <a name="rule-description"></a>Descrição da regra
Não defina a prioridade do processo como Ocioso. Os processos que `System.Diagnostics.ProcessPriorityClass.Idle` ocuparão a CPU quando, caso contrário, ficarão ociosos e, portanto, bloquearão o modo de espera.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Definir processos como `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Essa regra deve ser suprimida somente quando a prioridade de processo ociosa é necessária e as considerações de mobilidade podem ser ignoradas com segurança.