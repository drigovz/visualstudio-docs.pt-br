---
title: Localizar sua tarefa de depuração
description: Identificar o recurso do depurador que ajudará você a depurar seu aplicativo
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
ms.openlocfilehash: 7f8d971792fb55789fb6dcd7e0d90829ac723ba6
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817520"
---
# <a name="find-your-debugging-task-in-visual-studio"></a>Localizar sua tarefa de depuração no Visual Studio

Se você precisar de ajuda para mapear sua tarefa de depuração para o recurso correto do depurador do Visual Studio que é relevante, use os links fornecidos neste artigo. A lista de tarefas aqui inclui tarefas comuns, como pausar o código para depurar, inspecionar variáveis e enviar mensagens para a janela de **saída** . Se você precisar de uma visão geral dos recursos do depurador, consulte [primeiro examinar o depurador](debugger-feature-tour.md) .

## <a name="pause-running-code"></a>Pausar código em execução

### <a name="pause-running-code-to-inspect-a-line-of-code-that-may-contain-a-bug"></a>Pausar o código em execução para inspecionar uma linha de código que pode conter um bug

Definir um ponto de interrupção. Para obter mais informações, consulte [usando pontos de interrupção](using-breakpoints.md).

### <a name="pause-and-inspect-your-app-when-it-reaches-a-specific-state"></a>Pausar e inspecionar seu aplicativo quando ele atingir um estado específico

Tente um ponto de interrupção condicional para controlar onde e quando um ponto de interrupção é ativado usando a lógica condicional. Para obter mais informações, consulte [condições de ponto de interrupção](using-breakpoints.md#breakpoint-conditions).

### <a name="pause-code-only-when-a-specific-objects-property-or-value-changes"></a>Pausar o código somente quando a propriedade ou o valor de um objeto específico for alterado

Para C++, defina um [ponto de interrupção de dados](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). Para aplicativos que usam o .NET Core 3, você também pode definir um [ponto de interrupção de dados](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).

Caso contrário, C# para F# e somente, você pode [rastrear uma ID de objeto com um ponto de interrupção condicional](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

### <a name="pause-code-inside-a-loop-at-a-certain-iteration"></a>Pausar o código dentro de um loop em uma determinada iteração

Defina um ponto de interrupção usando **contagem de acesso** como uma condição. Para obter mais informações, consulte [contagem de acesso](using-breakpoints.md#hit-count).

### <a name="pause-code-at-the-start-of-a-function-when-you-know-the-function-name-but-not-its-location"></a>Pausar o código no início de uma função quando você souber o nome da função, mas não sua localização

Você pode fazer isso com um ponto de interrupção de função. Para obter mais informações, consulte [definir pontos de interrupção da função](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

### <a name="manage-and-keep-track-of-your-breakpoints"></a>Gerenciar e controlar seus pontos de interrupção

Use a janela **pontos de interrupção** . Para obter mais informações, consulte [gerenciar pontos de interrupção](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

### <a name="pause-code-and-debug-when-a-specific-handled-or-unhandled-exception-is-thrown"></a>Pausar o código e depurar quando uma exceção manipulada ou não tratada específica for gerada

Embora o auxiliar de exceção mostre onde ocorreu um erro, se você quiser pausar e depurar o erro específico, você pode [dizer ao depurador para interromper quando uma exceção for gerada](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

### <a name="set-a-breakpoint-from-the-call-stack"></a>Definir um ponto de interrupção da pilha de chamadas

Se você quiser pausar e depurar o código ao examinar o fluxo de execução ou a exibição de funções nas janelas da **pilha de chamadas** , consulte [definir um ponto de interrupção na janela pilha de chamadas](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

### <a name="pause-code-at-a-specific-assembly-instruction"></a>Pausar o código em uma instrução de assembly específica

Você pode fazer isso [definindo um ponto de interrupção na janela de desmontagem](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="inspect-data"></a>Inspecionar dados

### <a name="check-the-value-of-variables-while-running-your-app"></a>Verificar o valor das variáveis ao executar seu aplicativo

Passe o mouse sobre variáveis usando [dicas de dados](view-data-values-in-data-tips-in-the-code-editor.md) ou [Inspecione variáveis na janela automáticos e locais](autos-and-locals-windows.md).

### <a name="observe-the-changing-value-of-a-specific-variable"></a>Observar o valor de alteração de uma variável específica

Defina uma inspeção na variável. Para obter mais informações, consulte [definir uma inspeção em variáveis](watch-and-quickwatch-windows.md).

### <a name="view-strings-that-are-too-long-for-the-debugger-window"></a>Exibir cadeias de caracteres muito longas para a janela do depurador

Abra o [Visualizador de cadeia de caracteres](view-strings-visualizer.md) interno durante a depuração.

## <a name="additional-tasks"></a>Tarefas adicionais

### <a name="learn-the-commands-to-step-through-your-code-while-debugging"></a>Conheça os comandos para percorrer seu código durante a depuração

Para obter mais informações, consulte [navegar pelo código com o depurador](navigating-through-code-with-the-debugger.md).

### <a name="edit-code-during-a-debugging-session"></a>Editar código durante uma sessão de depuração

Use [Editar e continuar](edit-and-continue.md). Para o XAML, use o [Hot recarregamento de XAML](xaml-hot-reload.md).

### <a name="send-messages-to-the-output-window-without-modifying-code"></a>Enviar mensagens para a janela de saída sem modificar o código

Definir um tracepoint. Para obter mais informações, consulte [usando tracepoints](using-tracepoints.md).

### <a name="customize-information-shown-in-the-debugger"></a>Personalizar as informações mostradas no depurador

Talvez você queira mostrar informações que não sejam o tipo de objeto como o valor em janelas do depurador diferentes. Para C#, Visual Basic, F#e C++o código/CLI, use o atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Para opções mais avançadas, você também pode personalizar a interface do usuário criando um [visualizador personalizado](create-custom-visualizers-of-data.md).

Para o C++nativo, use a [estrutura NatVis](create-custom-views-of-native-objects.md).

### <a name="configure-debugger-settings"></a>Definir configurações do depurador

Para configurar opções do depurador e configurações do projeto do depurador, consulte [configurações e preparação do depurador](debugger-settings-and-preparation.md).

### <a name="debug-on-remote-machines"></a>Depurar em computadores remotos

Confira [Depuração remota](remote-debugging.md).

### <a name="debug-an-app-that-is-already-running"></a>Depurar um aplicativo que já está em execução

Consulte [anexar a um processo em execução](attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="debug-multithreaded-applications"></a>Depurar aplicativos multi-threaded

Consulte [depurar aplicativos multissegmentados](debug-multithreaded-applications-in-visual-studio.md).