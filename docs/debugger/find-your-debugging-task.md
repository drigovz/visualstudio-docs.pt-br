---
title: Perguntas frequentes-encontre seu recurso de depuração
description: Perguntas frequentes para ajudá-lo a identificar o recurso do depurador que ajudará você a depurar seu aplicativo
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
ms.openlocfilehash: a34aa926fca081a498173cd5fcc439a6b3886ba7
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728025"
---
# <a name="faq---find-the-debugging-feature-you-need-in-visual-studio"></a>Perguntas frequentes-encontre o recurso de depuração de que você precisa no Visual Studio

Se você precisar de ajuda para mapear sua tarefa de depuração para o recurso correto do depurador do Visual Studio que é relevante, use os links fornecidos neste artigo. A lista de tarefas aqui inclui tarefas comuns, como pausar o código para depurar, inspecionar variáveis e enviar mensagens para a janela de **saída** . Se você precisar de uma visão geral dos recursos do depurador, consulte [primeiro examinar o depurador](debugger-feature-tour.md) .

## <a name="fix-an-exception"></a>Corrigir uma exceção

- Consulte [corrigir uma exceção](write-better-code-with-visual-studio.md#fix-an-exception).

## <a name="pause-running-code"></a>Pausar código em execução

- **Pausar o código em execução para inspecionar uma linha de código que pode conter um bug**

  {2&gt;Defina um ponto de interrupção.&lt;2} Para obter mais informações, consulte [usando pontos de interrupção](using-breakpoints.md).

- **Pausar e inspecionar seu aplicativo quando ele atingir um estado específico**

  Tente um ponto de interrupção condicional para controlar onde e quando um ponto de interrupção é ativado usando a lógica condicional. Para obter mais informações, consulte [condições de ponto de interrupção](using-breakpoints.md#breakpoint-conditions).

- **Pausar o código somente quando a propriedade ou o valor de um objeto específico for alterado**

  Para C++, defina um [ponto de interrupção de dados](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus). 
  ::: moniker range=">= vs-2019"
  Para aplicativos que usam o .NET Core 3, você também pode definir um [ponto de interrupção de dados](using-breakpoints.md#BKMK_set_a_data_breakpoint_managed).
  ::: moniker-end

  Caso contrário, somente para C# e F #, você poderá [acompanhar uma ID de objeto com um ponto de interrupção condicional](using-breakpoints.md#using-object-ids-in-breakpoint-conditions-c-and-f).

- **Pausar o código dentro de um loop em uma determinada iteração**

  Defina um ponto de interrupção usando **contagem de acesso** como uma condição. Para obter mais informações, consulte [contagem de acesso](using-breakpoints.md#set-a-hit-count-condition).

- **Pausar o código no início de uma função quando você souber o nome da função, mas não sua localização**

  Você pode fazer isso com um ponto de interrupção de função. Para obter mais informações, consulte [definir pontos de interrupção da função](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Pausar o código no início de várias funções com o mesmo nome**

  Quando você tem várias funções com o mesmo nome (funções ou funções sobrecarregadas em projetos diferentes), você pode usar um [ponto de interrupção de função](using-breakpoints.md#BKMK_Set_a_breakpoint_in_a_source_file).

- **Gerenciar e controlar seus pontos de interrupção**

  Use a janela **pontos de interrupção** . Para obter mais informações, consulte [gerenciar pontos de interrupção](using-breakpoints.md#BKMK_Specify_advanced_properties_of_a_breakpoint_).

- **Pausar o código e depurar quando uma exceção manipulada ou não tratada específica for gerada**

  Embora o auxiliar de exceção mostre onde ocorreu um erro, se você quiser pausar e depurar o erro específico, você pode [dizer ao depurador para interromper quando uma exceção for gerada](managing-exceptions-with-the-debugger.md#tell-the-debugger-to-break-when-an-exception-is-thrown).

- **Definir um ponto de interrupção da pilha de chamadas**

  Se você quiser pausar e depurar o código ao examinar o fluxo de execução ou a exibição de funções nas janelas da **pilha de chamadas** , consulte [definir um ponto de interrupção na janela pilha de chamadas](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

- **Pausar o código em uma instrução de assembly específica**

  Você pode fazer isso [definindo um ponto de interrupção na janela de desmontagem](using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="execute-code"></a>Executar código

- **Conheça os comandos para percorrer seu código durante a depuração**

  Para obter mais informações, consulte [navegar pelo código com o depurador](navigating-through-code-with-the-debugger.md).

## <a name="inspect-data"></a>Inspecionar dados

- **Verificar o valor das variáveis ao executar seu aplicativo**

  Passe o mouse sobre variáveis usando [dicas de dados](view-data-values-in-data-tips-in-the-code-editor.md) ou [Inspecione variáveis na janela automáticos e locais](autos-and-locals-windows.md).

- **Observar o valor de alteração de uma variável específica**

  Defina uma inspeção na variável. Para obter mais informações, consulte [definir uma inspeção em variáveis](watch-and-quickwatch-windows.md).

- **Exibir cadeias de caracteres muito longas para a janela do depurador**

  Abra o [Visualizador de cadeia de caracteres](view-strings-visualizer.md) interno durante a depuração.

## <a name="debug-an-app-that-is-already-running"></a>Depurar um aplicativo que já está em execução

- Consulte [anexar a um processo em execução](attach-to-running-processes-with-the-visual-studio-debugger.md).

## <a name="debug-multithreaded-applications"></a>Depurar aplicativos multi-threaded

- Consulte [depurar aplicativos multissegmentados](debug-multithreaded-applications-in-visual-studio.md).

## <a name="configure-debugging"></a>Configurar a depuração

- **Definir configurações do depurador**

  Para configurar opções do depurador e configurações do projeto do depurador, consulte [configurações e preparação do depurador](debugger-settings-and-preparation.md).

- **Personalizar as informações mostradas no depurador**

  Talvez você queira mostrar informações que não sejam o tipo de objeto como o valor em janelas do depurador diferentes. Para o código C#, Visual Basic, F # e C++/CLI, use o atributo [DebuggerDisplay](using-the-debuggerdisplay-attribute.md) . Para opções mais avançadas, você também pode personalizar a interface do usuário criando um [visualizador personalizado](create-custom-visualizers-of-data.md).

  Para C++ nativo, use a [estrutura NatVis](create-custom-views-of-native-objects.md).

## <a name="additional-tasks"></a>Tarefas adicionais

- **Editar código durante uma sessão de depuração**

  Use [Editar e continuar](edit-and-continue.md). Para o XAML, use o [Hot recarregamento de XAML](../xaml-tools/xaml-hot-reload.md).

- **Enviar mensagens para a janela de saída sem modificar o código**

  Definir um tracepoint. Para obter mais informações, consulte [usando tracepoints](using-tracepoints.md).

- **Exibir a ordem na qual as funções são chamadas**

  Consulte [como exibir a pilha de chamadas](how-to-use-the-call-stack-window.md).

- **Depurar em computadores remotos**

  Consulte [depuração remota](remote-debugging.md).

- **Corrigir problemas de desempenho**

  Veja [a primeira olhada nas ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)
