---
title: Avisos de mobilidade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9f5606540d55c0a2c4257ff397ad77cc55624b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655977"
---
# <a name="mobility-warnings"></a>Avisos de mobilidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os avisos de mobilidade dão suporte ao uso de energia eficiente.

## <a name="in-this-section"></a>Nesta seção

|Regra|Descrição|
|----------|-----------------|
|[CA1600: não usar a prioridade de processo ociosa](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Não defina a prioridade do processo como Ocioso. Os processos que têm System.Diagnostics.ProcessPriorityClass.Idle ocuparão a CPU quando estariam ociosos e, assim, bloquearão a espera.|
|[CA1601: não usar temporizadores que impeçam alterações no estado de energia](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|A atividade periódica de alta frequência manterá a CPU ocupada e interferirá nos temporizadores ociosos que economizam energia e desligam monitores e discos rígidos.|
