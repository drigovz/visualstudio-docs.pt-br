---
title: Avisos de mobilidade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6061b614442d7bcb2f3465b1c40f35d583626c45
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167566"
---
# <a name="mobility-warnings"></a>Avisos de mobilidade
Os avisos de mobilidade dão suporte ao uso de energia eficiente.

## <a name="in-this-section"></a>Nesta seção

|Regra|DESCRIÇÃO|
|----------|-----------------|
|[CA1600: não usar a prioridade de processo ociosa](../code-quality/ca1600.md)|Não defina a prioridade do processo como Ocioso. Os processos que têm System.Diagnostics.ProcessPriorityClass.Idle ocuparão a CPU quando estariam ociosos e, assim, bloquearão a espera.|
|[CA1601: não usar temporizadores que impeçam alterações no estado de energia](../code-quality/ca1601.md)|A atividade periódica de alta frequência manterá a CPU ocupada e interferirá nos temporizadores ociosos que economizam energia e desligam monitores e discos rígidos.|
