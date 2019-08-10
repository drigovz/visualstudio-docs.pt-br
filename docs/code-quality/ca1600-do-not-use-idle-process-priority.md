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
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921817"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Não usar prioridade de processo ociosa

|||
|-|-|
|NomeDoTipo|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Categoria|Microsoft.Mobility|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Essa regra ocorre quando os processos são definidos `ProcessPriorityClass.Idle`como.

## <a name="rule-description"></a>Descrição da regra
Não defina a prioridade do processo como Ocioso. Os processos que `System.Diagnostics.ProcessPriorityClass.Idle` ocuparão a CPU quando, caso contrário, ficarão ociosos e, portanto, bloquearão o modo de espera.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Definir processos como `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Essa regra deve ser suprimida somente quando a prioridade de processo ociosa é necessária e as considerações de mobilidade podem ser ignoradas com segurança.