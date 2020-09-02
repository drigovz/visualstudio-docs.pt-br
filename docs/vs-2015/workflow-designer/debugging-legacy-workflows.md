---
title: Depurando fluxos de trabalho herdados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ae0a08e1623e1b90046d164d8bfe04eaf67229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656860"
---
# <a name="debugging-legacy-workflows"></a>Depurando fluxos de trabalho herdados
Se você estiver usando [!INCLUDE[wfd1](../includes/wfd1-md.md)] herdado no [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] para compilar aplicativos [!INCLUDE[wf](../includes/wf-md.md)] destinados ao .NET Framework 3.0 ou 3.5, poderá depurar seus fluxos de trabalho como qualquer outro programa definindo pontos de interrupção, anexando a processos e examinando threads e a pilha de chamadas. Você também tem a opção de depurar remotamente.

> [!NOTE]
> Se várias versões do Visual Studio tiverem sido instaladas e desinstaladas no computador, a depuração do WF3 poderá falhar com uma das duas possibilidades a seguir:
>
> - Os pontos de interrupção não foram atingidos.
>   - A seguinte mensagem é exibida:
>
>   **Não é possível iniciar a depuração no servidor Web. O depurador não está instalado corretamente.  Não é possível depurar o tipo de código solicitado.  Execute a instalação do para instalar ou reparar o depurador.**
>
>   Se qualquer um desses cenários ocorrer durante a depuração de fluxos de trabalho do .NET Framework 3.0 ou 3.5, execute um reparo da instalação do Visual Studio.

 [!INCLUDE[wf2](../includes/wf2-md.md)] integra-se com as seguintes [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] janelas de depuração padrão:

- **Ponto de interrupção**: funciona conforme o esperado, mas você especifica uma atividade para o nome da função.

- **Pilha de chamadas**: modificada para fornecer um contorno das atividades que foram executadas em uma instância de fluxo de trabalho. As entradas na janela **pilha de chamadas** são uma pesquisa de profundidade detalhada da execução de atividades. Você pode clicar duas vezes em uma entrada para colocar o foco na atividade selecionada.

- **Threads**: fornece a ID de instância da instância de fluxo de trabalho que está sendo depurada.

  O Visual Studio para Windows Foundation Workflow não oferece suporte aos seguintes recursos de depuração:

- Pontos de interrupção condicionais na superfície do designer.

- QuickWatch.

- Definir próxima instrução.

- Executar até o cursor.

- Editar e continuar.

- Depuração just-in-time.

- Depuração de modo misto.

## <a name="in-this-section"></a>Nesta seção
 [Chamar o depurador do Visual Studio para Windows Workflow Foundation (legados)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Desativando o depurador do Visual Studio para Windows Workflow Foundation (legados)](../workflow-designer/disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)

 [Como: Fluxos de trabalho de depuração ASP.NET-Based (legados)](../workflow-designer/how-to-debug-aspnet-based-workflows-legacy.md)

 [Como definir pontos de interrupção em fluxos de trabalho (herdado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)

 [Fluxos de trabalho de depuração de um computador remoto (legados)](../workflow-designer/debugging-workflows-from-a-remote-computer-legacy.md)

 [Opções de passo a passo em depuração (herdado)](../workflow-designer/debug-stepping-options-legacy.md)

 [Como: Altere a opção de avançar de depuração (o legados)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)