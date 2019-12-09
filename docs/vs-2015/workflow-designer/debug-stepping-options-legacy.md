---
title: Opções de depuração (herdadas) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 443cbac0ea9d74c61f24d6714162ec08e2906a62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656871"
---
# <a name="debug-stepping-options-legacy"></a>Opções de avançar de depuração (legados)
Este tópico descreve como depurar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] que têm atividades simultâneas em [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Ao depurar atividades herdadas que têm execução simultânea, como **ParallelActivity** ou **ConditionedActivityGroup**, você pode usar uma das duas opções a seguir para percorrer seu código.

- **Depuração de ramificação.** Esse modo de depuração permite que você percorra e depure uma ramificação específica de uma atividade composta, como a atividade **ParallelActivity** ou **ConditionalActivityGroup** . Quando você usa esta opção depuração, você não irá notar que uma alteração no controle ocorre devido à execução simultânea de outras atividades no fluxo de trabalho. As etapas do depurador somente com as atividades na ramificação atualmente selecionado quando outras atividades no fluxo de trabalho podem executar simultaneamente. Por exemplo, por padrão, a ramificação mais à esquerda em uma atividade **ParallelActivity** e a primeira atividade filho de uma atividade **ConditionedActivityGroup** são usadas para depuração. Se o usuário estiver interessado em depurar qualquer outra atividade de ramificação ou filhos, um ponto de interrupção explícito deve ser colocado na atividade de ramificação ou filho. Depuração continua naquela ramificação quando o ponto de interrupção é disparado.

- **Revisão da instância.** Este modo de avançar permite que você entrar completamente e depurar executar simultaneamente atividades no fluxo de trabalho. Com essa opção, você observará que uma alteração no controle ocorre ao executar simultaneamente atividades é executado dentro de fluxo de trabalho.

  Por padrão, a opção de avançar da ramificação é selecionada, e os usuários podem alternar entre as duas opções para depurar um fluxo de trabalho herdado.

  Você deve selecionar a opção de avançar da instância ao depurar fluxos de trabalho herdados do computador de estado.

## <a name="see-also"></a>Consulte também
 [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md) [como: alterar a opção de depuração (herdada)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)