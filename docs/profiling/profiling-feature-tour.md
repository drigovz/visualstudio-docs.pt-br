---
title: Medir o desempenho com ferramentas de criação de perfil
description: Dê uma olhada rápida em diferentes ferramentas de diagnóstico disponíveis no Visual Studio.
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688a446fbbaf1c2c56b9304576224a70f71064d8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79550109"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Início rápido: primeiro olhar sobre ferramentas de criação de perfil

O Visual Studio fornece uma variedade de ferramentas de criação de perfil para ajudá-lo a diagnosticar diferentes tipos de problemas de desempenho, dependendo do tipo do aplicativo.

As ferramentas de criação de perfil que podem ser acessadas durante uma sessão de depuração estão disponíveis na janela Ferramentas de Diagnóstico. A janela Ferramentas de Diagnóstico é exibida automaticamente, a menos que tenha sido desativada. Para abrir a janela, clique em **Depurar/Windows/Mostrar Ferramentas de Diagnóstico**. Com a janela aberta, é possível selecionar ferramentas para as quais você deseja coletar dados.

![Janela Ferramentas de Diagnóstico](../profiling/media/prof-tour-diagnostic-tools.png "Ferramentas de Diagnóstico")

Durante a depuração, é possível usar a janela **Ferramentas de Diagnóstico** para analisar o uso da CPU e de memória e exibir os eventos que mostram informações relacionadas ao desempenho.

![Exibição de resumo de ferramentas de diagnóstico](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Resumo das ferramentas de diagnóstico")

A janela **Ferramentas de Diagnóstico** costuma ser a maneira preferencial para criar perfis de aplicativos, mas para builds de Versão também é possível fazer uma análise post-mortem do aplicativo. Se você quiser obter mais informações sobre diferentes abordagens, confira [Executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Para ver o suporte à ferramentas de criação de perfil para tipos diferentes de aplicativo, confira [Qual ferramenta devo usar?](#which-tool-should-i-use).

> [!NOTE]
> Você pode usar as ferramentas post-mortem com o Windows 7 e posteriores. O Windows 8 ou posterior é necessário para executar ferramentas de criação de perfil com o depurador (janela **Ferramentas de Diagnóstico**).

## <a name="analyze-cpu-usage"></a>Analisar o uso de CPU

A ferramenta Uso da CPU é um bom lugar para começar a analisar o desempenho do aplicativo. Ela informará mais sobre os recursos de CPU que o aplicativo está consumindo. Para obter um passo a passo mais detalhado da ferramenta de uso da CPU, consulte Medir o [desempenho do aplicativo analisando o uso da CPU](../profiling/beginners-guide-to-performance-profiling.md).

Na exibição **Resumo** das Ferramentas de Diagnóstico, escolha **Habilitar Criação de Perfil da CPU** (é necessário estar em uma sessão de depuração).

![Habilite o uso da CPU nas Ferramentas de Diagnóstico](../profiling/media/prof-tour-enable-cpu-profiling.png "Ferramentas de diagnóstico permitem o uso da CPU")

Para usar a ferramenta com mais eficiência, defina dois pontos de interrupção no código: um no início e outro no final da função ou na região de código que você deseja analisar. Examine os dados de criação de perfil quando eles estiverem em pausa no segundo ponto de interrupção.

A exibição **Uso da CPU** mostra uma lista de funções ordenadas pela execução mais longa, com a função de execução mais longa na parte superior. Isso pode ajudar a levá-lo para as funções em que estão ocorrendo gargalos de desempenho.

![Exibição de uso da CPU de ferramentas de diagnóstico](../profiling/media/prof-tour-cpu-usage.png "Uso da CPU de ferramentas de diagnóstico")

Clique duas vezes em uma função de interesse e você verá uma exibição "borboleta" de três painéis mais detalhada, com a função selecionada no centro da janela, a função de chamada à esquerda e as funções chamadas à direita. A seção **Corpo da função** também mostra o tempo total (e o percentual de tempo) gasto no corpo da função, excluindo o tempo gasto nas funções de chamada e nas funções chamadas. Esses dados podem ajudá-lo a avaliar se a própria função é um gargalo de desempenho.

![Visão de chamada de chamada de ferramentas de diagnóstico callee "butterfly"](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Ferramenta de diagnóstico Chamada Chamada Callee View")

> [!TIP]
> Para ajudar a analisar o desempenho, você também pode usar [o PerfTips](#examine-performance-events-using-perftips) para passar pelo código e identificar quanto tempo leva funções ou blocos de código para ser concluído.

## <a name="examine-performance-events-using-perftips"></a>Examine eventos de desempenho usando PerfTips

Muitas vezes, a maneira mais fácil de visualizar informações de desempenho é usar [perfTips](../profiling/perftips.md). Usando perfTips, você pode visualizar informações de desempenho enquanto interage com seu código. É possível verificar informações como a duração do evento (medido da última pausa do depurador ou da inicialização do aplicativo). Por exemplo, se você passar pelo código (F10, F11), o PerfTips mostrará a duração de tempo de execução do aplicativo da operação da etapa anterior para a etapa atual.

![PerfTips do Tour de criação de perfil](../profiling/media/prof-tour-perf-tips.png "PerfTips do Tour de criação de perfil")

Você pode usar o PerfTips para examinar quanto tempo leva para um bloco de código ser executado, ou quanto tempo leva para uma única função ser concluída.

PerfTips mostram os mesmos eventos que também aparecem na visão **de Eventos** das Ferramentas de Diagnóstico. Na exibição **Eventos,** você pode visualizar diferentes eventos que ocorrem enquanto você está depurando, como a configuração de um ponto de ruptura ou uma operação de revisão de código.

![Exibição de eventos de ferramentas de diagnóstico](../profiling/media/prof-tour-events.png "Ferramentas de diagnóstico visualizam eventos")

 > [!NOTE]
 > Se você tiver o Visual Studio Enterprise, também poderá ver [eventos do IntelliTrace](../debugger/intellitrace.md) nessa guia.

## <a name="analyze-memory-usage"></a>Analisar o uso de memória

A janela **Ferramentas de Diagnóstico** também permite avaliar o uso da memória em seu aplicativo. Por exemplo, é possível examinar o número e tamanho dos objetos no heap. Para obter instruções mais detalhadas para analisar a memória, confira [Analisar uso da memória](../profiling/memory-usage.md).

Para analisar o uso da memória durante a depuração, você precisa tirar pelo menos um instantâneo de memória. Em geral, a melhor maneira de analisar a memória é usar dois instantâneos: o primeiro, logo antes de um problema de memória suspeito e o segundo instantâneo, logo após a ocorrência de um problema de memória suspeito. Depois, é possível exibir uma comparação dos dois instantâneos e ver exatamente o que mudou.

![Tire uma foto nas Ferramentas de Diagnóstico](../profiling/media/prof-tour-take-snapshots.gif "Ferramentas de diagnóstico tiram instantâneos")

Quando você seleciona um dos links de seta, você recebe uma visão diferencial do heap (uma seta vermelha para cima ![O uso da memória](../profiling/media/prof-tour-mem-usage-up-arrow.png "Aumento do uso da memória") mostra uma contagem crescente de objetos (à esquerda) ou um tamanho de pilha crescente (à direita)). Se você clicar no link à direita, terá uma exibição diferencial do heap, ordenada por objetos com maior aumento de tamanho de heap. Isso pode ajudá-lo a identificar problemas de memória. Por exemplo, na ilustração abaixo, os bytes usados por objetos `ClassHandlersStore` aumentaram em 3.492 bytes no segundo instantâneo.

![Visão de heap diff de ferramentas de diagnóstico](../profiling/media/prof-tour-mem-usage-diff-heap.png "Visão heap diff de ferramentas de diagnóstico")

Se você clicar no link à esquerda, na exibição **Uso de Memória**, a exibição do heap será organizada pela contagem de objetos: os objetos de um tipo específico com maior aumento em número são mostrados na parte superior (classificados pela coluna **Comparação de Contagem**).

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a>A versão do perfil é construída sem o depurador

As ferramentas de criação de perfil como Uso da CPU e Uso da Memória podem ser usadas com o depurador (veja as seções anteriores) ou é possível executar ferramentas de criação de perfil post-mortem usando o Criador de Perfil de Desempenho, cuja função é fornecer análise para builds de **Versão**. No Criador de Perfil de Desempenho, é possível coletar informações de diagnóstico durante a execução do aplicativo e, em seguida, examinar as informações coletadas depois que o aplicativo é interrompido. Para obter mais informações sobre essas diferentes abordagens, confira [Executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Ferramentas adicionais, como a [ferramenta .NET Object Allocation,](../profiling/dotnet-alloc-tool.md) também estão disponíveis no Profiler de desempenho.

![Criador de Perfil de Desempenho](../profiling/media/prof-tour-performance-profiler.png "Criador de Perfil de Desempenho")

Abra o Profiler de desempenho escolhendo **Debug** > **Performance Profiler**.

A janela permitirá selecionar várias ferramentas de criação de perfil em alguns cenários. Ferramentas como Uso da CPU podem fornecer dados complementares que podem ser usados para ajudar na análise. Você também pode usar o [profiler de linha de comando](../profiling/profile-apps-from-command-line.md) para habilitar cenários envolvendo várias ferramentas de criação de perfil.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Examinar os eventos de desempenho e de acessibilidade da interface do usuário (UWP)

Em seus aplicativos UWP, você pode ativar a **análise de interface do ui** na janela Ferramentas de **diagnóstico.** A ferramenta pesquisa problemas comuns de desempenho ou de acessibilidade, mostrando-os na exibição **Eventos** durante a depuração. As descrições de eventos fornecem informações que podem ajudar a resolver problemas.

![Ver eventos de análise de IA nas ferramentas de diagnóstico](../profiling/media/prof-tour-ui-analysis.png "Ferramentas de diagnóstico visualizam eventos de análise de ida e futura")

## <a name="analyze-resource-consumption-xaml"></a>Analisar o consumo de recursos (XAML)

Em aplicativos XAML, como aplicativos WPF da área de trabalho do Windows e aplicativos UWP, é possível analisar o consumo de recursos usando a ferramenta Linha do Tempo do Aplicativo. Por exemplo, é possível analisar o tempo gasto pelo aplicativo para preparar quadros de interface do usuário (layout e renderização), atender a solicitações de rede e de disco e em cenários como inicialização do aplicativo, carregamento de página e redimensionamento do Windows. Para usar a ferramenta, escolha **Linha do Tempo do Aplicativo** no Criador de Perfil de Desempenho e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário com um problema de consumo de recursos suspeito e escolha **Parar coleta** para gerar o relatório.

Taxas de quadros baixas no gráfico **Taxa de transferência visual** podem corresponder aos problemas visuais vistos ao executar o aplicativo. Da mesma forma, números elevados no gráfico **Utilização de thread de interface do usuário** também podem corresponder a problemas de capacidade de resposta da interface do usuário. No relatório, é possível selecionar um período com um problema de desempenho suspeito e, em seguida, examinar as atividades detalhadas de thread de interface do usuário na exibição Detalhes da linha do tempo (painel inferior).

![Ferramenta de criação de perfil da linha do tempo do aplicativo](../profiling/media/prof-tour-application-timeline.gif "Cronograma do aplicativo do tour de criação de perfil")

Na exibição de detalhes da Linha do Tempo, você pode encontrar informações como o tipo de atividade (ou o elemento de UI envolvido) juntamente com a duração da atividade. Por exemplo, na ilustração, um evento **Layout** de um controle Grade usa 57,53 ms.

Para obter mais informações, consulte [Linha do Tempo do Aplicativo](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analisar o uso da GPU (Direct3D)

Em aplicativos Direct3D (os componentes Direct3D devem estar no C++), é possível examinar a atividade na GPU e analisar problemas de desempenho. Para obter mais informações, consulte [Uso da GPU](/visualstudio/debugger/graphics/gpu-usage). Para usar a ferramenta, escolha **Uso da GPU** no Criador de Perfil de Desempenho e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário de interesse na criação de perfil e, em seguida, escolha **Parar coleta** para gerar um relatório.

Ao selecionar um período nos gráficos e escolher **Exibir detalhes**, uma exibição detalhada será exibida no painel inferior. Na exibição detalhada, é possível examinar as atividades que estão ocorrendo em cada CPU e GPU. Selecione eventos no painel inferior para obter pop-ups na linha do tempo. Por exemplo, selecione o eventos **Presente** para exibir pop-ups da chamada **Presente**. (As linhas verticais Vsync cinza-claras podem ser usadas como referência para entender se algumas chamadas **Presente** não têm Vsync. Deve haver uma chamada **Presente** entre cada dois Vsyncs para que o aplicativo atinja progressivamente 60 FPS.)

![Ferramenta de criação de perfil de uso de GPU](../profiling/media/prof-tour-gpu-usage.png "Uso da GPU diag")

Também é possível usar os gráficos para determinar se há gargalos de desempenho limitados à CPU ou à GPU.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Analisar o desempenho (JavaScript UWP)

Para aplicativos UWP, é possível usar a ferramenta Memória JavaScript e a ferramenta Capacidade de Resposta de IU em HTML.

A ferramenta Memória JavaScript é semelhante à ferramenta Uso de Memória disponível para outros tipos de aplicativos. É possível usar essa ferramenta para entender o uso de memória e encontrar perdas de memória no aplicativo. Para obter mais detalhes sobre a ferramenta, consulte [Memória JavaScript](../profiling/javascript-memory.md).

![Ferramenta de criação de perfil de memória JavaScript](../profiling/media/diagjsmemory.png "DiagJSMemory")

Para diagnosticar a capacidade de resposta de IU, tempo de carregamento lento e atualizações visuais lentas em aplicativos UWP, use a ferramenta Capacidade de Resposta de IU em HTML. O uso é semelhante à ferramenta Linha do Tempo do Aplicativo para outros tipos de aplicativos. Para obter mais informações, consulte [Capacidade de resposta de interface do usuário HTML](../profiling/html-ui-responsiveness.md).

![Ferramenta de criação de perfil de capacidade de resposta de UI HTML](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Analisar o uso de rede (UWP)

Em aplicativos UWP, é possível analisar as operações de rede executadas usando a API `Windows.Web.Http`. Essa ferramenta pode ajudá-lo a resolver problemas, como problemas de acesso e autenticação, uso de cache incorreto e desempenho insatisfatório de exibição e download. Para usar a ferramenta, escolha **Rede** no Criador de Perfil de Desempenho e, em seguida, escolha **Iniciar**. No aplicativo, percorra o cenário que usa `Windows.Web.Http` e escolha **Parar coleta** para gerar o relatório.

![Ferramenta de criação de perfil de uso de rede](../profiling/media/prof-tour-network-usage.png "Uso da rede Diag")

Selecione uma operação na exibição de resumo para exibir mais detalhes.

![Informações detalhadas na ferramenta Deuso de Rede](../profiling/media/prof-tour-network-usage-details.png "Detalhes de uso da rede Diag")

Para obter mais informações, consulte [Uso de rede](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Analisar o desempenho (ferramentas herdadas)

::: moniker range="vs-2017"
Se você precisar de recursos, como instrumentação, que não estão atualmente presentes nas ferramentas Uso da CPU ou Uso de Memória, e estiver executando aplicativos de área de trabalho ou aplicativos ASP.NET, poderá usar o Gerenciador de Desempenho para a criação de perfil. (Sem suporte em aplicativos UWP). Para obter mais informações, consulte [Gerenciador de Desempenho](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
No Visual Studio 2019, o Explorador de Desempenho legado e ferramentas de criação de perfil relacionadas, como o Assistente de Desempenho, foram dobradas no Profiler de desempenho, que você pode abrir usando **o Debug** > **Performance Profiler**. No Profiler de desempenho, as ferramentas de diagnóstico disponíveis dependem do alvo escolhido e do projeto de startup aberta e atual. A ferramenta de uso da CPU fornece o recurso de amostragem anteriormente suportado no Assistente de Desempenho. A ferramenta Instrumentação fornece o recurso de criação de perfil instrumentado (para contagem e duração de chamadas precisas) que estava no Assistente de Desempenho. Ferramentas de memória adicionais também aparecem no Profiler de desempenho.
::: moniker-end

![Ferramenta Explorador de desempenho](../profiling/media/prof-tour-performance-explorer.png "Performance Explorer")

## <a name="which-tool-should-i-use"></a>Qual ferramenta devo usar?

Eis aqui uma tabela que lista as diferentes ferramentas que o Visual Studio oferece e os diferentes tipos de projeto com os quais você poderá usá-las:

::: moniker range=">=vs-2019"
|Ferramenta de Desempenho|Área de trabalho do Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Uso da CPU](../profiling/cpu-usage.md)|sim|sim|sim|
|[Uso de Memória](../profiling/memory-usage.md)|sim|sim|sim|
|[.NET Alocação de objetos](../profiling/dotnet-alloc-tool.md)|sim (somente.NET)|sim|sim|
|[Uso de GPU](/visualstudio/debugger/graphics/gpu-usage)|sim|sim|não|
|[Linha do tempo do aplicativo](../profiling/application-timeline.md)|sim|sim|não|
|[PerfTips](../profiling/perftips.md)|sim|sim para XAML, não para HTML|sim|
|[Gerenciador de Desempenho](../profiling/performance-explorer.md)|sim|não|sim|
|[IntelliTrace](../debugger/intellitrace.md)|.NET com Visual Studio Enterprise somente|.NET com Visual Studio Enterprise somente|.NET com Visual Studio Enterprise somente|
::: moniker-end

::: moniker range="vs-2017"
|Ferramenta de Desempenho|Área de trabalho do Windows|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[Uso da CPU](../profiling/cpu-usage.md)|sim|sim|sim|
|[Uso de Memória](../profiling/memory-usage.md)|sim|sim|sim|
|[Uso de GPU](/visualstudio/debugger/graphics/gpu-usage)|sim|sim|não|
|[Linha do tempo do aplicativo](../profiling/application-timeline.md)|sim|sim|não|
|[PerfTips](../profiling/perftips.md)|sim|sim para XAML, não para HTML|sim|
|[Gerenciador de Desempenho](../profiling/performance-explorer.md)|sim|não|sim|
|[IntelliTrace](../debugger/intellitrace.md)|.NET com Visual Studio Enterprise somente|.NET com Visual Studio Enterprise somente|.NET com Visual Studio Enterprise somente|
|[Uso de Rede](../profiling/network-usage.md)|não|sim|não|
|[Resposta da UI HTML](../profiling/html-ui-responsiveness.md)|não|sim para HTML, não para XAML|não|
|[Memória JavaScript](../profiling/javascript-memory.md)|não|sim para HTML, não para XAML|não|
::: moniker-end


## <a name="see-also"></a>Confira também
- [Depurando no Visual Studio](../debugger/debugger-feature-tour.md)
