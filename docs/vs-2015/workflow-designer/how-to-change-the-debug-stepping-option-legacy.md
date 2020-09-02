---
title: Como alterar a opção de depuração (herdada) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663447"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Como: Altere a opção de avançar de depuração (o legados)
Este tópico descreve como modificar a opção de avançar de depuração para aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] em novas [!INCLUDE[wfd1](../includes/wfd1-md.md)] que têm ações simultâneas. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Ao depurar atividades herdadas que têm execução simultânea, como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções para percorrer seu código.

 Siga estas etapas para alterar a opção de avançar de depuração no seu projeto herdado de fluxo de trabalho.

## <a name="procedures"></a>Procedimentos

#### <a name="to-change-the-debug-stepping-option"></a>Para alterar a opção de avançar de depuração

1. Inicie o Visual Studio.

2. Abrir um projeto existente herdado de fluxo de trabalho ou criar um novo projeto que empreguem atividades simultâneas e que tem como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

3. No menu **fluxo de trabalho** do herdado [!INCLUDE[wfd2](../includes/wfd2-md.md)] , aponte para **depurar**e, em seguida, aponte para opções de **revisão**.

4. Selecione **instância** ou **ramificação**.

## <a name="see-also"></a>Consulte Também
 Depurando opções de depuração de [fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md) [(Herdado)](../workflow-designer/debug-stepping-options-legacy.md)