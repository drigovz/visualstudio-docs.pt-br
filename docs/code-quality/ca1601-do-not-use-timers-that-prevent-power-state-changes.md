---
title: 'CA1601: Não usar temporizadores que impedem alterações no estado de energia'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b3c3fe41332d488d180ddafbedfe29da1a3855e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921783"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Não usar temporizadores que impedem alterações no estado de energia

|||
|-|-|
|NomeDoTipo|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Categoria|Microsoft.Mobility|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um temporizador tem um intervalo definido para ocorrer mais de uma vez por segundo.

## <a name="rule-description"></a>Descrição da regra
Não sondar com mais frequência do que uma vez por segundo ou usar temporizadores que ocorrem com mais frequência do que uma vez por segundo. A atividade periódica de alta frequência manterá a CPU ocupada e interferirá nos temporizadores ociosos que economizam energia e desligam monitores e discos rígidos.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Defina intervalos de timer para ocorrer menos de uma vez por segundo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Essa regra deve ser suprimida somente se o acionamento do temporizador mais de uma vez por segundo for necessário e as considerações de mobilidade puderem ser ignoradas com segurança.