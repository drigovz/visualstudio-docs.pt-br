---
title: Encontre sua tarefa de depuração
description: Identifique o recurso de depurador que vai ajudá-lo a depurar seu aplicativo
ms.custom: ''
ms.date: 10/01/2019
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], find your feature
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 792b5e2d40f7299bf019fd3f9c86697bf008c391
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302178"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Encontre sua tarefa de depuração no Visual Studio

Se você precisar de ajuda para mapear sua tarefa de depuração para o recurso correto do depurador visual studio que é relevante, use os links fornecidos neste artigo. A lista de tarefas aqui inclui tarefas comuns, como pausar código para depurar, inspecionar variáveis e enviar mensagens para a janela **Saída.** Se você precisar de uma visão geral dos recursos do depurador, consulte [Primeiro, veja o depurador.](debugger-feature-tour.md)

## <a name="pause-running-code"></a>Pausa código de execução

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pause o código de execução para inspecionar uma linha de código que pode conter um bug

{2&gt;Defina um ponto de interrupção.&lt;2} Para obter mais informações, consulte [Usando pontos de interrupção](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pause e inspecione seu aplicativo quando ele chegar a um estado específico

Tente um ponto de ruptura condicional para controlar onde e quando um ponto de ruptura é ativado usando lógica condicional. Para obter mais informações, consulte [condições de breakpoint](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pausar o código somente quando a propriedade ou valor de um objeto específico mudar

Para C++, defina um [ponto de ruptura de dados](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
::: moniker range=">= vs-2019"
Para aplicativos usando o .NET Core 3, você também pode definir um [ponto de ruptura de dados](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
::: moniker-end

Caso contrário, apenas para C# e F#, você pode [rastrear um ID de objeto com um ponto de ruptura condicional](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Código de pausa dentro de um loop em uma certa iteração

Defina um ponto de ruptura usando **a contagem de hits** como condição. Para obter mais informações, consulte [Contagem de hits](using-breakpoints.md#set-a-hit-count-condition).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Código de pausa no início de uma função quando você sabe o nome da função, mas não sua localização

Você pode fazer isso com um ponto de ruptura de função. Para obter mais informações, consulte [Set function breakpoints](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="pause-code-at-the-start-of-multiple-functions-with-the-same-name"></a>Código de pausa no início de múltiplas funções com o mesmo nome

Quando você tem várias funções com o mesmo nome (funções ou funções sobrecarregadas em diferentes projetos), você pode usar um [ponto de ruptura de função](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Gerencie e acompanhe seus pontos de interrupção

Use a janela **Pontos de interrupção.** Para obter mais informações, consulte [Gerenciar pontos de interrupção](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Desfaça o código de pausa e depuraquando uma exceção específica tratada ou não tratada é lançada

Embora o Helper de exceção mostre onde ocorreu um erro, se você quiser pausar e depurar o erro específico, você pode [dizer ao depurador para quebrar quando uma exceção é lançada](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Defina um ponto de ruptura da pilha de chamadas

Se você quiser pausar e depurar código ao examinar o fluxo de execução ou visualizar funções nas janelas **do Call Stack,** consulte [Definir um ponto de ruptura na janela Pilha de chamadas](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Código de pausa em uma instrução de montagem específica

Você pode fazer isso [definindo um ponto de ruptura da janela Desmontagem](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Executar código

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Aprenda os comandos a passar pelo seu código durante a depuração

Para obter mais informações, consulte [Navegar código com o depurador](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspecionar os dados

### <a name="check-the-value-of-variables-while-running-your-app"></a>Verifique o valor das variáveis durante a execução do seu aplicativo

Passar o tempo sobre variáveis usando [dicas de dados](view-data-values-in-data-tips-in-the-code-editor.md) ou inspecionar variáveis na janela [Autos e Locais](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observe o valor de mudança de uma variável específica

Defina um relógio na variável. Para obter mais informações, consulte [Definir um relógio sobre variáveis](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Exibir strings que são muito longas para a janela de depurador

Abra o [visualizador](view-strings-visualizer.md) de string incorporado durante a depuração.

## <a name="configure-debugging"></a>Configurar a depuração

### <a name="customize-information-shown-in-the-debugger"></a>Personalize as informações mostradas no depurador

Você pode querer mostrar informações que não o tipo de objeto como o valor em diferentes janelas de depurador. Para c#, visual básico, f#e código C++/CLI, use o atributo [DebuggerDisplay.](using-the-debuggerdisplay-attribute.md) Para opções mais avançadas, você também pode personalizar a ida e outra, criando um [visualizador personalizado.](create-custom-visualizers-of-data.md)

Para C++nativo, use a [estrutura NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Configurar configurações de depurador

Para configurar as opções de depurador e as configurações do projeto de depuração, consulte [configurações e preparação do Depurador](debugger-settings-and-preparation.md).

## <a name="additional-tasks"></a>Tarefas adicionais

### <a name="fix-an-exception"></a>Corrigir uma exceção

Consulte [Corrigir uma exceção](write-better-code-with-visual-studio.md#fix-an-exception).

### <a name="edit-code-during-a-debugging-session"></a>Editar código durante uma sessão de depuração

Use [Editar e continuar](edit-and-continue.md). Para XAML, use [XAML Hot Reload](../xaml-tools/xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Envie mensagens para a janela Saída sem modificar o código

Defina um ponto de rastreamento. Para obter mais informações, consulte [Usando tracepoints](using-tracepoints.md).

## <a name="view-the-order-in-which-functions-are-called"></a>Veja a ordem em que as funções são chamadas

Veja [como visualizar a pilha de chamadas](how-to-use-the-call-stack-window.md).

### <a name="debug-on-remote-machines"></a>Depuração em máquinas remotas

Consulte [Depuração remota](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Depurar um aplicativo que já está em execução

Consulte [Anexar a um processo em execução](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Depurar aplicativos multi-threaded

Consulte [Debug aplicativos multithreaded](debug-multithreaded-applications-in-visual-studio.md).

### <a name="fix-performance-issues"></a>Corrigir problemas de desempenho

Veja [primeiro as ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)