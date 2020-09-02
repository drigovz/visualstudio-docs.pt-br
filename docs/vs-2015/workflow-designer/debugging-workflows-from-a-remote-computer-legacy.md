---
title: Depurando fluxos de trabalho de um computador remoto (Herdado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656852"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Fluxos de trabalho de depuração de um computador remoto (legados)
Este tópico descreve como depurar aplicativos herdadas remotos de [!INCLUDE[wf](../includes/wf-md.md)] que são criados com [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando seu aplicativo precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Quando você instala [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] o, uma das opções de instalação do componente é instalar o [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] depurador para o [!INCLUDE[wf](../includes/wf-md.md)] . Isso instala os componentes de depuração remota. Esses componentes de depuração remota devem ser instalados no computador que você está definido para depuração remota de fluxo de trabalho.

 Além disso, o assembly que contém a definição de fluxo de trabalho de fluxo de trabalho herdado que você está depurando em um computador remoto deve ser instalado no cachê global de assemblies (GAC) do computador local que você está depurando de. Por exemplo, se um fluxo de trabalho herdado estiver em execução em um computador remoto A e você estiver depurando-o do computador local B, a definição de fluxo de trabalho deverá estar presente no GAC do computador B. Isso permite que o designer Desserialize e exiba no computador B a marcação de fluxo de trabalho do fluxo de trabalho que está sendo executado remotamente no computador A. Para obter mais informações sobre o cache de assembly global, consulte a biblioteca MSDN.

 [!INCLUDE[wf2](../includes/wf2-md.md)] a depuração remota funciona da mesma forma que a depuração remota para outros [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] componentes. Para obter mais informações, consulte [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] depuração remota na biblioteca MSDN.

## <a name="see-also"></a>Consulte Também
 [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)