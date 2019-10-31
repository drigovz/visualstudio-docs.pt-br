---
title: Dicas e truques no depurador
description: Saiba mais sobre alguns dos recursos menos conhecidos com suporte do depurador do Visual Studio
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188622"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Aprenda dicas e truques de produtividade para o depurador no Visual Studio

Leia este tópico para aprender algumas dicas de produtividade e truques para o depurador do Visual Studio. Para examinar os recursos básicos do depurador, consulte [a primeira olhada no depurador](../debugger/debugger-feature-tour.md). Neste tópico, abordaremos algumas áreas que não estão incluídas no tour pelos recursos.

## <a name="pin-data-tips"></a>Fixar dicas de dados

Se você passar o mouse sobre dicas de dados durante a depuração, convém fixar a dica de dados da variável para fornecer acesso rápido. A variável permanece fixada mesmo após a reinicialização. Para fixar a dica de dados, clique no ícone de pino ao passar o mouse sobre ele. Você pode fixar várias variáveis.

![Fixando uma dica de dados](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Editar seu código e continuar a depuraçãoC#(, VB C++,)

Na maioria dos idiomas com suporte no Visual Studio, você pode editar seu código no meio de uma sessão de depuração e continuar a depuração. Para usar esse recurso, clique em seu código com o cursor enquanto estiver em pausa no depurador, faça edições e pressione **F5**, **F10**ou **F11** para continuar a depuração.

![Editar e continuar a depuração](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Para obter mais informações sobre como usar o recurso e as limitações de recursos, consulte [Editar e continuar](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Editar código XAML e continuar a depuração

Para modificar o código XAML durante uma sessão de depuração, consulte [gravar e depurar o código XAML em execução com o Hot recarregamento de XAML](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Problemas de depuração que são difíceis de reproduzir

Se for difícil ou demorado recriar um estado específico em seu aplicativo, considere se o uso de um ponto de interrupção condicional pode ajudar. Você pode usar [pontos de interrupção condicionais](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) e filtrar pontos de interrupção para evitar dividir o código do aplicativo até que o aplicativo Insira um estado desejado (como um estado no qual uma variável está armazenando dados inválidos). Você pode definir condições usando expressões, filtros, contagens de acertos e assim por diante.

#### <a name="to-create-a-conditional-breakpoint"></a>Para criar um ponto de interrupção condicional

1. Clique com o botão direito do mouse em um ícone de ponto de interrupção (a bola vermelha) e escolha **condições**.

2. Na janela **configurações de ponto de interrupção** , digite uma expressão.

    ![Ponto de interrupção condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Se você estiver interessado em outro tipo de condição, selecione **Filtrar** em vez de **expressão condicional** na caixa de diálogo **configurações de ponto de interrupção** e siga as dicas de filtro.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Configurar os dados a serem mostrados no depurador

Para C#, Visual Basic e C++ (C++somente código/CLI), você pode informar ao depurador quais informações mostrar usando o atributo [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) . Para C++ o código, você pode fazer o mesmo usando [visualizações de Natvis](create-custom-views-of-native-objects.md).

## <a name="change-the-execution-flow"></a>Alterar o fluxo de execução

Com o depurador pausado em uma linha de código, use o mouse para pegar o ponteiro de seta amarela à esquerda. Mova o ponteiro de seta amarela para um ponto diferente no caminho de execução de código. Em seguida, use F5 ou um comando Step para continuar a execução do aplicativo.

![Mover o ponteiro de execução](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Mover o ponteiro de execução")

Alterando o fluxo de execução, você pode fazer coisas como testar caminhos de execução de código diferentes ou executar novamente o código sem reiniciar o depurador.

> [!WARNING]
> Geralmente, você precisa ter cuidado com esse recurso. Um aviso é exibido na dica de ferramenta. Outros avisos também podem ser exibidos. Mover o ponteiro não pode reverter seu aplicativo para um estado de aplicativo anterior.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Rastrear um objeto fora do escopo (C#, Visual Basic)

É fácil exibir variáveis usando janelas do depurador como a janela **Watch** . No entanto, quando uma variável sai do escopo na janela **Watch** , você pode notar que ela está esmaecida. Em alguns cenários de aplicativo, o valor de uma variável pode ser alterado mesmo quando a variável está fora do escopo, e você talvez queira vê-la de maneira mais próxima (por exemplo, uma variável pode obter lixo coletado). Você pode acompanhar a variável criando uma ID de objeto para ela na janela **Watch** .

#### <a name="to-create-an-object-id"></a>Para criar uma ID de objeto

1. Defina um ponto de interrupção próximo a uma variável que você deseja rastrear.

2. Inicie o depurador (**F5**) e pare no ponto de interrupção.

3. Localize a variável na janela **locais** (**depurar > locais do Windows >** ), clique com o botão direito do mouse na variável e selecione **criar ID de objeto**.

    ![Criar uma ID de objeto](../debugger/media/dbg-tips-watch-create-object-id.png "Createobjectid")

4. Você deve ver um **$** mais um número na janela **locais** . Essa variável é a ID do objeto.

5. Clique com o botão direito do mouse na variável ID de objeto e escolha **Adicionar inspeção**.

Para obter mais informações, consulte [criar uma ID de objeto](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Exibir valores de retorno para funções

Para exibir valores de retorno para suas funções, examine as funções que aparecem na janela de **autons** enquanto você está passando pelo código. Para ver o valor de retorno de uma função, certifique-se de que a função em que você está interessado já tenha sido executada (pressione **F10** uma vez se você estiver atualmente parado na chamada de função). Se a janela for fechada, use **Debug > o Windows > autos** para abrir a janela de **automóveis** .

![Janela de automóveis](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Além disso, você pode inserir funções na janela **imediata** para exibir valores de retorno. (Abra-o usando **Debug > Windows > Immediate**.)

![Janela Imediata](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Você também pode usar o [pseudovariables](../debugger/pseudovariables.md) na janela **Watch** e **Immediate** , como `$ReturnValue`.

## <a name="string_visualizer"></a>Inspecionar cadeias de caracteres em um visualizador

Ao trabalhar com cadeias de caracteres, pode ser útil exibir toda a cadeia de caracteres formatada. Para exibir uma cadeia de caracteres de texto sem formatação, XML, HTML ou JSON, clique no ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Ícone do Visualizador") ao passar o mouse sobre uma variável que contém um valor de cadeia de caracteres.

![Abrir um visualizador de cadeia de caracteres](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Um visualizador de cadeia de caracteres pode ajudá-lo a descobrir se uma cadeia de caracteres está malformada, dependendo do tipo de cadeia de caracteres. Por exemplo, um campo de **valor** em branco indica que a cadeia de caracteres não é reconhecida pelo tipo de visualizador. Para obter mais informações, consulte [caixa de diálogo Visualizador de cadeia de caracteres](../debugger/string-visualizer-dialog-box.md).

![Visualizador de cadeia de caracteres JSON](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Para alguns outros tipos, como objetos DataSet e DataTable que aparecem nas janelas do depurador, você também pode abrir um visualizador interno.

## <a name="break-into-code-on-handled-exceptions"></a>Dividir em código em exceções manipuladas

O depurador divide seu código em exceções sem tratamento. No entanto, exceções manipuladas (como exceções que ocorrem em um bloco de `try/catch`) também podem ser uma fonte de bugs e você talvez queira investigar quando elas ocorrem. Você pode configurar o depurador para dividir o código para exceções manipuladas também, Configurando opções na caixa de diálogo **configurações de exceção** . Abra essa caixa de diálogo escolhendo **depurar > configurações de exceção do Windows >** .

A caixa de diálogo **configurações de exceção** permite que você informe o depurador para dividir o código em exceções específicas. Na ilustração abaixo, o depurador divide seu código sempre que um `System.NullReferenceException` ocorre. Para obter mais informações, consulte [Gerenciando exceções](../debugger/managing-exceptions-with-the-debugger.md).

![Caixa de diálogo Configurações de exceção](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Depurar deadlocks e condições de corrida

Se você precisar depurar os tipos de problemas que são comuns a aplicativos multissegmentados, ele geralmente ajuda a exibir o local dos threads durante a depuração. Você pode fazer isso facilmente usando o botão **Mostrar threads no código-fonte** .

#### <a name="to-show-threads-in-your-source-code"></a>Para mostrar threads em seu código-fonte

1. Durante a depuração, clique no botão **Mostrar threads no código-fonte** ![Mostrar threads na fonte](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") na barra de ferramentas **depurar** .

2. Examine a medianiz no lado esquerdo da janela. Nessa linha, você verá um ![marcador de thread](../debugger/media/dbg-thread-marker.png "ThreadMarker") com ícone de *marcador de thread* que se assemelha a dois threads de tecido. O marcador de thread indica que um thread está parado nesse local.

    Observe que um marcador de thread pode ser parcialmente escondido por um ponto de interrupção.

3. Passe o ponteiro sobre o marcador de thread. Um DataTip aparece. O DataTip mostra o nome e o número de ID do thread para cada thread parado.

    Você também pode exibir o local dos threads na [janela pilhas paralelas](../debugger/get-started-debugging-multithreaded-apps.md).

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Examinar as cargas para serviços Web e recursos de rede (UWP)

Em aplicativos UWP, você pode analisar as operações de rede executadas usando a API `Windows.Web.Http`. Você pode usar essa ferramenta para ajudar a depurar os serviços Web e os recursos de rede. Para usar a ferramenta, selecione **depurar > criador de perfil de desempenho**. Selecione **rede**e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário que usa `Windows.Web.Http` e escolha **Parar coleta** para gerar o relatório.

![Ferramenta de criação de perfil de uso de rede](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Selecione uma operação na exibição de resumo para exibir mais detalhes.

![Informações detalhadas na ferramenta de uso de rede](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Para obter mais informações, consulte [Uso de rede](../profiling/network-usage.md).
::: moniker-end

## <a name="modules_window"></a>Familiarize-se com o modo como o depurador se anexa aoC#seu C++aplicativo (, F#, Visual Basic,)

Para anexar ao seu aplicativo em execução, o depurador carrega arquivos de símbolo (. pdb) gerados para exatamente a mesma compilação do aplicativo que você está tentando depurar. Em alguns cenários, um pouco de conhecimento dos arquivos de símbolo pode ser útil. Você pode examinar como o Visual Studio carrega arquivos de símbolo usando a janela **módulos** .

Abra a janela **módulos** durante a depuração selecionando **depurar > módulos do Windows >** . A janela **módulos** pode informar quais módulos o depurador está tratando como código do usuário, ou [*meu código*](../debugger/just-my-code.md), e o status de carregamento do símbolo do módulo. Na maioria dos cenários, o depurador localiza automaticamente arquivos de símbolo para o código do usuário, mas se você quiser entrar (ou depurar) código .NET, código do sistema ou código de biblioteca de terceiros, etapas adicionais serão necessárias para obter os arquivos de símbolo corretos.

![Exibir informações de símbolo na janela módulos](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Você pode carregar informações de símbolo diretamente na janela **módulos** clicando com o botão direito do mouse e escolhendo **carregar símbolos**.

Às vezes, os desenvolvedores de aplicativos enviam aplicativos sem os arquivos de símbolo correspondentes (para reduzir a superfície), mas mantêm uma cópia dos arquivos de símbolo correspondentes para a compilação para que possam depurar uma versão lançada posteriormente.

Para descobrir como o depurador classifica o código como código de usuário, consulte [apenas meu código](../debugger/just-my-code.md). Para saber mais sobre arquivos de símbolo, consulte [especificar símbolo (. pdb) e arquivos de origem no depurador do Visual Studio](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Saiba mais

Para obter dicas e truques adicionais e informações mais detalhadas, consulte estas postagens no blog:

- [7 hackers menos conhecidos para depuração no Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 Gems ocultas no Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Consulte também

[Atalhos de teclado](../ide/productivity-shortcuts.md)
