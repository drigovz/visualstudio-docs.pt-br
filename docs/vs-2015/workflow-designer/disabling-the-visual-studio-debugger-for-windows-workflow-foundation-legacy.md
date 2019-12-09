---
title: Desabilitando o depurador para Windows Workflow Foundation (Herdado) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656781"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados)
Este tópico descreve como desativar o depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que usa o arquivo de configuração para criar aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] em [!INCLUDE[wfd1](../includes/wfd1-md.md)]herdado. Use [!INCLUDE[wfd2](../includes/wfd2-md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Por padrão, o depurador de [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] para [!INCLUDE[wf](../includes/wf-md.md)] é habilitado para um processo host. Para desabilitar a depuração do fluxo de trabalho, você deve desativá-la explicitamente adicionando uma entrada "DisableWorkflowDebugging" **\<switches elemento >** na seção **\<system. Diagnostics >** do arquivo de configuração do host.

 O exemplo a seguir mostra como modificar o arquivo de configuração do host para desativar a depuração de fluxo de trabalho.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Consulte também
 [Invocando o depurador do Visual Studio para depuração Windows Workflow Foundation (herdada) de fluxos de](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)